<style lang="scss" scoped>
  @import "../assets/scss/colors.scss";

  .active {
    color: $red;
  }

</style>

<template>

  <div>
    <!-- +1 moves sequence left, -1 moves it right.  user probably expects the reverse, so we're reversing steps rotated sign -->
    <label>Rotation: {{ stepsRotated * -1 }}</label>
    <button 
    :class='{ active: stepsRotated * -1 < 0}'
    class="fa fa-caret-left decrement" @click="updateRotation(+1)" /> 
    <button 
    :class='{ active: stepsRotated * -1 > 0}'
    class="fa fa-caret-right" @click="updateRotation(-1)" />
  </div>

</template>

<script>

  export default {
    name: 'Rotation',
    props: {
      stepsRotated: Number,
      rotationMagnitude: Number
    },
    methods: {
      updateRotation(magnitude) {
        this.$emit('rotation-updated', magnitude)
      }
    }
  }

</script>

