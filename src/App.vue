<template>
  <div id="app">
    <TwitterStreamApp />
  </div>
</template>

<script>
import TwitterStreamApp from './components/TwitterStreamApp.vue'

export default {
  name: 'App',
  components: {
    TwitterStreamApp
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
