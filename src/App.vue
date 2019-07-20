<template>
  <div id="app">
    <Header/>
    <Timer/>
  </div>
</template>

<script>
import Timer from './components/Timer.vue'
import Header from './components/Header.vue'

export default {
  name: 'app',
  components: {
    Timer,
    Header
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: 	#ffffff;
  background-color: #45b3e0;
  height: 100vh;
}
body{
  margin: 0%;
}
</style>
