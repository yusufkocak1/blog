<template>
  <div id="app">

    <HelloWorld msg="Welcome "/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  height: 100vh;
}

body {
  background-color: #212121;
}
</style>
