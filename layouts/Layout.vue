<template>
  <div>
    <Header :onclick="onClick" />
    <Nav :navs="navs" />
    <SearchBox v-if="$site.themeConfig.search" />
    <Tag :tags="tags" :onclick="onClick" />
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
import SearchBox from '../components/SearchBox'
import Tag from '../components/Tag'
import Home from '../components/Home'
import Page from '../components/Page'
import Footer from '../components/Footer'

export default {
  components: {
    Header: Header,
    Nav: Nav,
    SearchBox: SearchBox,
    Tag: Tag,
    Home: Home,
    Page: Page,
    Footer: Footer,
  },
  data: function () {
    return {
      navs: [],
      list: [],
    }
  },
  computed: {
    tags: function () {
      let tags = []
      let flag = {}
      for (let i = 0; i < this.$site.pages.length; i++) {
        let page = this.$site.pages[i]
        let tag = decodeURI(page.path.split('/')[1])
        if (page.path !== '/' && !flag[tag]) {
          flag[tag] = true
          tags.push(tag)
        }
      }
      return tags
    },
  },
  mounted: function () {
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
      } else if (page.frontmatter.home === undefined || page.frontmatter.home === null || page.frontmatter.home === false) {
          this.list = undefined
          break
      }
    }
    this.navs = this.$site.themeConfig.nav
  },
  methods: {
    onClick: function (arg) {
      this.list = []
      for (let i = 0; i < this.$site.pages.length; i++) {
        let page = this.$site.pages[i]
        if (page.path !== '/') {
          let tag = decodeURI(page.path.split('/')[1])
          if (arg === '/') {
            this.list.push({
              tag: tag,
              title: page.title,
              path: page.path,
            })
          } else if (arg === tag) {
            this.list.push({
              tag: arg,
              title: page.title,
              path: page.path,
            })
          }
        } else if (arg === "/" && (page.frontmatter.home === undefined || page.frontmatter.home === null || page.frontmatter.home === false)) {
            this.list = undefined
            break
        }
      }
      this.$router.push({ path: '/' })
    }
  },
}
</script>

<style lang="stylus" scoped>

</style>