<template>
<div class="item">
  <a class="link" :href="url"><div><slot /></div><div>›</div></a>
</div>
</template>

<script>
export default {
 name: "GwiMenuDefaultItem",
 props: {
   url: {
     type: String,
     required: true
   }
 }
}
</script>

<style scoped lang="scss">
  @import '../theme/attributes/common/_colors';
  @import '../theme/attributes/common/_spacings';
  @import '../theme/attributes/common/_breakpoints';
  @import '../theme/mixins/_link';

  .link {
    display: flex;
    justify-content: space-between;
    padding: $spacing__component-inner--default / 2;
    @media all and(max-width: $breakpoint__s) {
      padding: $spacing__component-inner--default / 3;
    }
    @include link();
  }
</style>
