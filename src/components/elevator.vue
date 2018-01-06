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
    floors: {
      type: Number,
      default: 0,
    },
    currentTick: {
      type: Number,
      default: 0,
    },
    requested: {
      type: Boolean,
      default: true,
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
  watch: {
    currentTick() {
      if (this.moving) {
        this.currentFloor += 1;
        this.$emit('elevator.moving', this.moving, this.direction, this.currentFloor);
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
