<template>
  <div id="app">
    <Coordinates />
  </div>
</template>

<script>
import Coordinates from './components/Coordinates.vue'

export default {
  name: 'app',
  components: {
    Coordinates
  }
}
</script>

<style>
body {
  margin: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #2c3e50;
  color: #fefefe;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
</style>
