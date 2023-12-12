<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App" />
  <YurimHappy mss="happy Yurimmmmmmmm" />
</template>

<script>
import HelloWorld from './componentsg/HelloWorld.vue'
import YurimHappy from './components/Yurim.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    YurimHappy
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
