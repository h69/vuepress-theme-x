<template>
  <div>
    <Header :links="links" :onclick="onClick" />
    <Nav :navs="navs" :onclick="onClick" />
    <main>
      <Home v-if="$page.path === '/'" :list="list" />
      <Page v-else />
    </main>
    <Footer />
  </div>
</template>

<script>
import Header from '../components/Header'
import Nav from '../components/Nav'
import Footer from '../components/Footer'
import Home from '../components/Home'
import Page from '../components/Page'

export default {
  components: {
    Header: Header,
    Nav: Nav,
    Footer: Footer,
    Home: Home,
    Page: Page,
  },
  data: function () {
    return {
      links: [],
      list: [],
    }
  },
  computed: {
    navs: function () {
      let navs = []
      let flag = {}
      for (let i = 0; i < this.$site.pages.length; i++) {
        let page = this.$site.pages[i]
        let nav = decodeURI(page.path.split('/')[1])
        if (page.path !== '/' && !flag[nav]) {
          flag[nav] = true
          navs.push(nav)
        }
      }
      return navs
    },
  },
  mounted: function () {
    console.log(this.$site)
    this.list = []
    for (let i = 0; i < this.$site.pages.length; i++) {
      let page = this.$site.pages[i]
      if (page.path !== '/') {
        let tag = decodeURI(page.path.split('/')[1])
        this.list.push({
          tag: tag,
          title: page.title,
          path: page.path,
        })
      }
    }
    this.links = this.$site.themeConfig.nav
  },
  methods: {
    onClick: function (nav) {
      this.list = []
      for (let i = 0; i < this.$site.pages.length; i++) {
        let page = this.$site.pages[i]
        if (page.path !== '/') {
          let tag = decodeURI(page.path.split('/')[1])
          if (nav === '/') {
            this.list.push({
              tag: tag,
              title: page.title,
              path: page.path,
            })
          } else if (nav === tag) {
            this.list.push({
              tag: nav,
              title: page.title,
              path: page.path,
            })
          }
        }
      }
      this.$router.push({ path: '/' })
    }
  },
}
</script>

<style lang="stylus" scoped>

</style>