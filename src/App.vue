<template>
  <div id="app">
    <HelloWorld :isLogged="isLogged"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data () {
    return {
      isLogged: false
    }
  }
}
</script>

<style>
#app {
  height: 100vh;
  width: 375px;
  font-family: 'Inter', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #47474A;
  margin-top: 31px;
}
</style>
