<template>
  <div
    :class="{
      'gwi-card--no-padding': !padding,
      ['gwi-card gwi-card--' + level]: true,
      ['gwi-card__layout--' + layout]: layout
    }"
  >
    <slot />
  </div>
</template>

<script>
  export default {
    props: {
      padding: {
        default: true,
        type: [String, Boolean],
        validator: (value) => {
          return typeof value === 'boolean' || value === 'true' || value === 'false'
        }
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
      }
    },
    computed: {
      noPaddingInner () {
        return typeof this.noPadding === 'boolean' ? this.noPadding : this.noPadding === 'true'
      }
    }
  }
</script>

<style lang="scss">
  @import '../theme/index';
  .gwi-card {
    background-color: white;
    margin: 0 auto 30px auto;
    padding: $spacing__components-inner--default;
    /*overflow: hidden;*/
    @media screen and (max-width: 600px){
      padding: $spacing__components-inner--small;
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
