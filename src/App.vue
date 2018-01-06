<template>
  <div id="app">
    <nav>
      <select v-model="floorRequested">
        <option v-for="floor in floors" :key="floor">{{ floor }}</option>
      </select>
      <button type="button" @click.stop.prevent="sendRequest">Send Request</button>
    </nav>
    <elevator
      v-for="(elevator, index) in elevators" :key="index"
      :floors="floors"
      :bottom-floor="bottomFloor"
      :current-tick="currentTick"
      :requested="requested"
      :id="elevator.id"></elevator>
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
      floors: 14,
      requested: false,
      elevators: data,
      started: false,
      interval: null,
      currentTick: 0,
    }
  },
  mounted() {
    // Once mounted, begin a timer function that will relay states
    // to the various elevators
    this.started = true;
  },
  methods: {
    relayInformationToElevators() {
      if (this.started) {
        this.currentTick = Date.now();
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
    },
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

nav {
  margin: 20px;
  text-align: left;
}

.elevator {
  float: left;
  margin: 20px;
}
</style>
