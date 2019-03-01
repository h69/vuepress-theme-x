<template>
  <div>
    <div v-for="(page, index) in pages" :key="index">
      <router-link :to="page.path">{{ page.title }}</router-link>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    pages: function () {
      console.log(this.$site)
      return this.$site.pages.filter((item) => (item.path !== '/'))
    }
  },
}
</script>
