<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <HelloWorld msg="Welcome to Your Vue.js App"/>
    <!-- <Transition/> -->
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
// import Transition from './components/Transition.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    // Transition
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  margin-top: 0px;
  background-color: black;
}
</style>
