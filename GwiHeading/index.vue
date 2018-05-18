<script>
  export default {
    render: function (createElement) {
      return createElement('h' + this.markupLevelInternal, {class: {
        'gwi-text__heading': true,
          'gwi-spacing__heading-margin--top': this.marginTop,['gwi-text__heading--' + this.stylingLevel]: true
      }}, this.$slots.default)
    },
    props: {
      markupLevel: {
        default: 3
      },
      stylingLevel: {
        default: 3
      },
      marginTop: {
        type: [Boolean],
        default: true
      }
    },
    computed: {
      markupLevelInternal () {
        return Number(this.markupLevel)
      }
    }
  }
</script>

<style lang="scss">
  @import '../theme/index';

  @import '../theme/attributes/components/GwiHeading';

  .gwi-spacing {
    &__heading-margin {
      &--top {
        &:first-child {
          margin-top: $spacing__heading-top-first--default;
          @media screen and (max-width: $breakpoint__s) {
            margin-top: $spacing__heading-top-first--small;
          }
        }
      }
    }
  }
  .gwi-text {
    &__heading {
      color: $color__text--highlight;
      margin-top: $spacing__heading-top--default;
      margin-bottom: $spacing__heading-bottom--default;
      text-shadow: $typography__shadow--heading;

      @media screen and (max-width: $breakpoint__s) {
        margin-bottom: $spacing__heading-bottom--small;
      }
      &--1 {
        @include heading--1;
      }
      &--2 {
        @include heading--2;
      }
      &--3 {
        @include heading--3;
      }
      &--4 {
        @include heading--4;
      }
    }
  }
</style>
