<template>
  <div class="main" v-if="isLoaded">
    <the-nav />
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data: () => ({
    isLoaded: false
  }),
  mounted () {
    this.$nextTick(() => {
      this.$nuxt.$loading.start()
      setTimeout(() => {
        this.$nuxt.$loading.finish()
        this.isLoaded = true
      }, 5000)
    })
  }
}
</script>

<style>
.main {
  background-color: #ededed;
  padding: 40px;
  height: calc(100vh - 80px);
}
html {
  font-size: 10px;
}
body {
  margin: 0;
}
</style>