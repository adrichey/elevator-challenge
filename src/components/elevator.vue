<template>
  <div class="elevator">
  </div>
</template>

<script>
export default {
  name: 'elevator',
  props: {
    currentTick: {
      type: Number,
      default: 0,
    },
  },
  data () {
    return {
      floors: 1,
      isMoving: false,
      direction: 'up',
      doorsOpen: false,
    }
  },
  watch: {
    currentTick() {
      // TO DO - Flesh this out
    }
  }
}
</script>

<style scoped>
</style>
