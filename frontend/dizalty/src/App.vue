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
@import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap');

#app {
  font-family: Roboto, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  margin-top: 40px;
}

body{
    background: url("../public/images/ban5.jpeg") no-repeat center center fixed;
    background-size: cover;
    background-clip: padding-box;
}
</style>
