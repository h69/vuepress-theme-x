<template>
  <div>
    <Header />
    <main>
      <component :is="component" />
    </main>
    <Footer />
  </div>
</template>

<script>
import Header from '../components/Header'
import Footer from '../components/Footer'
import Blog from '../components/Blog'
import Article from '../components/Article'

export default {
  components: {
    Header: Header,
    Footer: Footer,
    Blog: Blog,
    Article: Article,
  },
  computed: {
    component: function () {
      switch (this.$page.path) {
        case '/': return Blog
        default: return Article
      }
    }
  }
}
</script>
