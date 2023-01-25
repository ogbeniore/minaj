<template>
  <div class="main" v-if="isLoaded">
    <!-- <the-nav /> -->
    <first-slide />
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
  padding: 40px;
}
html {
  font-size: 10px;
}
body {
  background-color: #fcf6fa;
  margin: 0;
}
</style>