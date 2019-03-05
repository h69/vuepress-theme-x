<template>
  <header class="header">
    <div class="title" @click="onclick('/')">{{ $site.title }}</div>
    <div class="links">
      <a class="link" v-for="(link, index) in links" :key="index" :href="link.link" target="_blank">
        <img v-if="link.text === 'github'" src="../images/github.png" />
        <span v-else>{{ link.text }}</span>
      </a>
    </div>
  </header>
</template>

<script>
export default {
  props: [
    'links',
    'onclick',
  ],
}
</script>

<style lang="stylus" scoped>
.header
  margin 0 auto 50px auto
  text-align center

.title
  cursor pointer
  margin 0 0 20px 0

.link 
  cursor pointer
  margin 0 8px

.link img
  width 15px
  height 15px
</style>