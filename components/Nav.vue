<template>
  <nav class="navs">
    <div class="nav" v-for="(nav, index) in navs" :key="index" @click="onclick(nav)"><a>{{ nav }}</a></div>
  </nav>
</template>

<script>
export default {
  props: [
    'navs',
    'onclick',
  ],
}
</script>

<style lang="stylus" scoped>
.navs
  margin 50px 0 50px 0
  overflow auto
  
.nav
  float left
  cursor pointer
  margin 5px 20px 5px 0
  padding 4px 10px 4px 10px
  font-size 12px
  border-radius 3px
  background-color lighten($accentColor, 90%)
  &:hover
    background-color lighten($accentColor, 80%)
</style>
  