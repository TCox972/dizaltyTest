<template>
  <div id="app">
    <TestComp></TestComp>
  </div>
</template>

<script>
import TestComp from './components/TestComp.vue'

export default {
  name: 'App',
  components: {
    TestComp
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
  margin-top: 40px;
}

body{
    background-image: url("../public/images/ban5.jpeg");
}
</style>
