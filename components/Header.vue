<template>
  <header class="header">
    <div class="title" @click="onclick('/')">{{ $site.title }}</div>
  </header>
</template>

<script>
export default {
  props: [
    'onclick',
  ],
}
</script>

<style lang="stylus" scoped>
.header
  margin 0 auto 20px auto
  text-align center

.title
  cursor pointer
</style>