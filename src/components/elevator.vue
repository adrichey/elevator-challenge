<template>
  <div class="elevator">
  </div>
</template>

<script>
export default {
  name: 'elevator',
  props: {
    id: {
      type: Number,
      required: true,
    },
    bottomFloor: {
      type: Number,
      required: true,
    },
    floors: {
      type: Number,
      required: true,
    },
    currentTick: {
      type: Number,
      default: 0,
    },
    requested: {
      type: Boolean,
      default: false,
    },
  },
  data () {
    return {
      moving: false,
      direction: 'up',
      doorsOpen: false,
      currentFloor: 1,
    }
  },
  methods: {
    moveOneFloor() {
      if (this.doorsOpen) {
        return this.currentFloor;
      }

      if (this.direction === 'up' && this.currentFloor < this.floors) {
        this.currentFloor += 1;
      } else if (this.direction === 'down' && this.currentFloor > this.bottomFloor) {
        this.currentFloor -= 1;
      }

      this.$emit('elevator.moving', this.moving, this.direction, this.currentFloor);

      return this.currentFloor();
    }
  },
  watch: {
    currentTick() {
      if (this.moving) {
        this.moveOneFloor();
      }
    },
    doorsOpen() {
      this.$emit('elevator.doorsOpen', this.doorsOpen, this.currentFloor);
    }
  }
}
</script>

<style scoped>
</style>
