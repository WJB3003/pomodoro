<template>
  <div id="app">
    <div class="container">
      <Header/>
      <Timer/>
    </div>
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
  -moz-osx-font-smoothing: grayscale;
  color: 	#ffffff;
  background-color: #45b3e0;
  height: 100vh;
}
.container{
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}
body{
  margin: 0%;
}
</style>
