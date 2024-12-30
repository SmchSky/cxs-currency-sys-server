<script>
import {getExternalLinkList} from "@/api/main";
import {getCache, setCache} from "@/utils/cache";
import {FOOTER_LINK_LIST_KEY} from "@/utils/cache_constent";

export default {
  name: "main-footer",
  data() {
    return {
      linkList: []
    }
  },
  mounted() {
    this.init()
  },
  methods: {
    init() {
      getExternalLinkList().then(res => {
        this.linkList = res.data
        setCache(FOOTER_LINK_LIST_KEY, res.data)
      }).catch(() => {
        this.linkList = getCache(FOOTER_LINK_LIST_KEY)
      })
    }
  }
}
</script>

<style scoped lang="less">
.footer-all {
  width: 100%;
  height: 70px;
  background-color: white;
  padding-top: 10px;
  box-sizing: border-box;
  position: fixed;
  left: 0;
  bottom: 0;

  div, ul {
    height: 30px;
  }

  .friend-link {
    width: 100%;
    display: flex;
    justify-content: center;

    li {
      margin: 0 10px;
    }
  }

  .beian {
    text-align: center;
  }
}

ol, ul, li {
  list-style: none;
}
</style>
