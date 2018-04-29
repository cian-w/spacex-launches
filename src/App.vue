<template>
  <div id="app">
    <space-x/>
  </div>
</template>

<script>
import SpaceX from './components/SpaceX'

export default {
  name: 'App',
  components: {
    SpaceX
  }
}
</script>

<style>
#app {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
