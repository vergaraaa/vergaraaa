<!-- key: c27e34ca-3f52-472c-ba36-496b812a3da1 -->
<!-- reset: https://api.countapi.xyz/set/c27e34ca-3f52-472c-ba36-496b812a3da1?value=0 -->
<template>
  <div v-if="loading">...</div>
  <div v-else>
    felicidades, eres el chismoso <strong>#{{visitors}}</strong>
  </div>
</template>

<script>
import countapi from 'countapi-js';

export default {
  name: 'App',
  data() {
    return {
      visitors: 0,
      loading: false,
    }
  },
  async mounted() {
    this.loading = true
    const visitors = await countapi.hit('c27e34ca-3f52-472c-ba36-496b812a3da1')
    this.visitors = visitors.value
    this.loading = false
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
