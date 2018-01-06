<template>
  <div class="elevator">
    <h1>Elevator {{ elevatorId }}</h1>
    <p>Is Moving: {{ moving }}</p>
    <p>Direction: {{ direction }}</p>
    <p>Current Floor: {{ currentFloor }}</p>
    <p>Doors Open: {{ doorsOpen }}</p>
  </div>
</template>

<script>
export default {
  name: 'elevator',
  props: {
    elevatorId: {
      type: String,
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
    moving: {
      type: Boolean,
      default: false,
    },
    direction: {
      type: String,
      default: 'up',
    },
    doorsOpen: {
      type: Boolean,
      default: false,
    },
    currentFloor: {
      type: Number,
      default: 1,
    },
    maintenance: {
      type: Boolean,
      default: false,
    },
    floorsTraveled: {
      type: Number,
      default: 0,
    },
    trips: {
      type: Number,
      default: 0,
    },
  },

  methods: {
    /**
     * Fulfills #2: Each elevator will report as it moves from floor to floor
     */
    moveOneFloor() {
      if (this.doorsOpen) {
        return this.currentFloor;
      }

      if (this.direction === 'up' && this.currentFloor < this.floors) {
        this.currentFloor += 1;
      } else if (this.direction === 'down' && this.currentFloor > this.bottomFloor) {
        this.currentFloor -= 1;
      }

      this.$emit('elevator.moving', this.elevatorId, this.moving, this.direction, this.currentFloor);

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
      this.$emit('elevator.doorsOpen', this.elevatorId, this.doorsOpen, this.currentFloor);
    },
  }
}
</script>