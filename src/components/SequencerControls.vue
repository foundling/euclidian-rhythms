<template>
  <div class="sequencer-controls">

    <slot></slot>
    <!--
    <label>steps:</label>
    <input
    type="number"
    min="0"
    :value="stepCount"
    v-on:change="updateStepCount(parseInt($event.target.value))" />

    <label>rotate</label>
    <button class="fas fa-caret-left" @click="decrementRotation" />
    <button class="fas fa-caret-right" @click="incrementRotation" />

    <span> direction: </span>
    <i @click="reverseDirection('counter-clockwise')"
    :class="{
      'selected': direction === 'counter-clockwise',
      'fas fa-arrow-alt-circle-left': direction === 'counter-clockwise',
      'far fa-arrow-alt-circle-left': direction === 'clockwise'
    }"
    class="reverse-direction" />

    <i @click="reverseDirection('clockwise')"
    :class="{
      'selected': direction === 'clockwise',
      'fas fa-arrow-alt-circle-right': direction === 'clockwise',
      'far fa-arrow-alt-circle-right': direction === 'counter-clockwise'
    }"
    class="reverse-direction" />

    <span>pulse increment: </span>
    <select 
    v-model="currentPulseMode"
    @change="updatePulseMode(currentPulseMode)">
      <option v-for="mode in pulseModes" :name="mode">{{ mode }}</option>
    </select>
    -->

  </div>
</template>

<style lang="scss" scoped>
  .sequencer-controls {
    .reverse-direction {
      color: lightgray;
    }
  }
</style>

<script>
  export default {
    name: 'SequencerControls',
    props: {
    },
    data() {
      return {
        currentPulseMode: '+1',
        pulseModes: [ '+1', '-1', 'random' ]
      }
    },
    methods: {
      updatePulseMode(newPulseMode) {
        this.$emit('sequencer-controls-pulse-mode-updated', newPulseMode)
      },
      updateStepCount(newStepCount) {
        this.$emit('sequencer-controls-update-step-count', newStepCount)
      },
      incrementRotation() {
        this.$emit('sequencer-controls-rotated', +1)
      },
      decrementRotation() {
        this.$emit('sequencer-controls-rotated', -1)
      },
      reverseDirection(direction) {
        if (direction !== this.direction)
          this.$emit('sequencer-controls-direction-changed', direction)
      }
    }
  }
</script>
