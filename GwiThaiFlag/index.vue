<template>
  <div class="container" :style="{height: `${height}px`, width: `${height * 1.5}px`}">
    <div class="row red">&nbsp;</div>
    <div class="row white">&nbsp;</div>
    <div class="row blue">&nbsp;</div>
    <div class="row blue">&nbsp;</div>
    <div class="row white">&nbsp;</div>
    <div class="row red">&nbsp;</div>
  </div>
</template>

<script>
  export default {
    name: "GwiThaiFlag",
    props: {
      height: {
        default: 500,
        type: Number,
      }
    }
  }
</script>

<style scoped lang="scss">
  .container {
    display: flex;
    flex-direction: column;
    position: relative;
  }
  .row {
    display: flex;
    height: 16.666666666666667%;
    align-items: stretch;
  }
  .red {
    background-color: red;
    flex-grow: 1;
  }
  .white {
    background-color: white;
    flex-grow: 1;
  }
  .blue {
    background-color: blue;
    flex-grow: 1;
  }
</style>
