<template>
  <div id="app">
    <elevator></elevator>
  </div>
</template>

<script>
import elevator from './components/elevator';
import data from './assets/data';

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
      elevators: data,
      started: false,
      interval: null,
    }
  },
  mounted() {
    // Once mounted, begin a timer function that will relay states
    // to the various elevators
    this.started = true;
  },
  methods: {
    relayInformationToElevators() {
      const elevatorsLength = this.elevators.length;
      let i;
      for (i = 0; i < elevatorsLength; i += 1) {
        // Set data
      }
    }
  },
  watch: {
    started(flag) {
      if (flag) {
        this.interval = setInterval(this.relayInformationToElevators, 1000);
      } else {
        clearInterval(this.interval);
      }
    }
  }
};
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
