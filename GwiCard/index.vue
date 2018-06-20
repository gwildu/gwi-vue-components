<template>
  <div
    :class="{
      'gwi-card--no-padding': !padding,
      'gwi-spacing__margin--top': marginTop,
      'gwi-spacing__margin--bottom': marginBottom,
      ['gwi-card gwi-card--' + level]: true,
      ['gwi-card__layout--' + layout]: layout
    }"
  ><slot /></div>
</template>

<script>
  export default {
    props: {
      padding: {
        default: true,
        type: [Boolean]
      },
      level: {
        default: 1
      },
      layout: {
        validator: (value) => {
          const allowedValues = [
            'fill',
            'stretch'
          ]
          return allowedValues.indexOf(value) > -1
        },
        default: 'stretch'
      },
      marginTop: {
        type: [Boolean],
        default: false
      },
      marginBottom: {
        type: [Boolean],
        default: true
      }
    }
  }
</script>

<style lang="scss">
  @import '../theme/index';

  @import './index';

  .gwi-card {
    background-color: $card__color--background;
    margin: 0 auto;
    padding: $spacing__component-inner--default;
    line-height: $typography__line-height--default;
    /*overflow: hidden;*/
    @media screen and (max-width: $breakpoint__s){
      padding: $spacing__component-inner--small;
    }
    &--no-padding {
      padding: 0;
    }
    &--1 {
      @include card-frame(1);
    }
    &--2 {
      @include card-frame(2);
    }
    &--3 {
      @include card-frame(3);
    }
    &--4 {
      @include card-frame(4);
    }
    &--5 {
      @include card-frame(5);
    }

    &__layout {
      &--fill {
        display: inline-block;
      }

      &--stretch {
        width: 100%;
      }
    }
    img {
      line-height: 0;
    }
  }

</style>
