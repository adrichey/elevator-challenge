<template>
  <div id="app">
    <elevator></elevator>
  </div>
</template>

<script>
import elevator from './components/elevator'

export default {
  name: 'app',
  components: {
    elevator
  },
  data () {
    return {
      bottomFloor: 1,
      floors: 1,
      isRequested: false,
      elevators: [
        { isMoving }
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
