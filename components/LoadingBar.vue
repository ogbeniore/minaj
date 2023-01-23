<template>
  <div v-if="loading" class="loading-page">
    <p>
      <span>T</span>
      <span>i</span>
      <span>n</span>
      <span>a</span>
      <span>d</span>
      <span>e</span>
      <span>&</span>
      <span>O</span>
      <span>l</span>
      <span>u</span>
      <span>m</span>
      <span>i</span>
      <span>d</span>
      <span>e</span>
    </p>
  </div>
</template>

<script>
export default {
  data: () => ({
    loading: false
  }),
  methods: {
    start () {
      this.loading = true
    },
    finish () {
      this.loading = false
    }
  }
}
</script>

<style scoped lang="scss">
  .loading-page {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: #F5F9E9;
    text-align: center;
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 100;
    p {
      font-family: 'Cutive Mono', cursive;
      font-size: 40px;
      line-height: 64px;
      color: #00A36C;
      font-weight: 700;
      span {
        display: inline-block;
        margin: 0 5px;
        @for $i from 0 through 15 {
          &:nth-child(#{$i + 1}) {
            filter: blur(0);
            animation: blur-text 1.2s (#{calc($i/15)})+s infinite linear alternate;
          }
        }
      }
    }

    @keyframes blur-text {
      0% {filter: blur(0);}
      100% {filter: blur(3px);}
    }
  }
</style>
