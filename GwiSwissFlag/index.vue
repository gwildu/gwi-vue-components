<template>
  <div class="container" :style="{height: `${height}px`, width: `${height}px`}">
    <div class="row red">&nbsp;</div>
    <div class="row">
      <div class="red">&nbsp;</div>
      <div class="red">&nbsp;</div>
      <div class="white">&nbsp;</div>
      <div class="red">&nbsp;</div>
      <div class="red">&nbsp;</div>
    </div>
    <div class="row">
      <div class="red">&nbsp;</div>
      <div class="white">&nbsp;</div>
      <div class="white">&nbsp;</div>
      <div class="white">&nbsp;</div>
      <div class="red">&nbsp;</div>
    </div>
    <div class="row">
      <div class="red">&nbsp;</div>
      <div class="red">&nbsp;</div>
      <div class="white">&nbsp;</div>
      <div class="red">&nbsp;</div>
      <div class="red">&nbsp;</div>
    </div>
    <div class="red row">&nbsp;</div>
  </div>
</template>

<script>
  export default {
    name: 'GwiSwissFlag',
    props: {
      height: {
        default: 500,
        type: Number,
      }
    }
  }
</script>

<style scoped>
  .container {
    display: flex;
    flex-direction: column;
    position: relative;
  }
  .row {
    display: flex;
    height: 20%;
    align-content: stretch;
  }
  .red {
    background-color: red;
    flex-grow: 1;
  }
  .white {
    background-color: white;
    flex-grow: 1;
  }
</style>
