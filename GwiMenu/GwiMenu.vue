<template>
  <GwiCard :padding="true" level="4">
    <ul>
      <li class="level1" v-for="item in items">
        <component :is="itemComponent" :url="item.url" >{{item.displayName}}</component>
        <ul class="subItems" v-if="item.items">
          <li class="level2" v-for="subItem in item.items">
            <component :is="itemComponent" :url="subItem.url" >{{subItem.displayName}}</component>
          </li>
        </ul>
      </li>
    </ul>
  </GwiCard>
</template>

<script>
import GwiCard from '../GwiCard'
import GwiMenuDefaultItem from './GwiMenuDefaultItem'

export default {
  name: "GwiMenu",
  components: {GwiCard, GwiMenuDefaultItem},
  props: {
    items: {
      type: Array
    },
    itemComponent: {
      default() {
        return GwiMenuDefaultItem
      }
    }
  }
}
</script>

<style scoped lang="scss">
  @import '../theme/attributes/common/_colors';
  @import '../theme/attributes/common/_spacings';

  .level1, .level2 {
    border-bottom: 1px solid $color__line--main;
  }

  .level1 {
    &:last-of-type {
      border-bottom: none;
    }
  }

  .level2 {
    &:first-of-type {
      border-top: 1px solid $color__line--main;
    }
    &:last-of-type {
      border-bottom: none;
    }
  }

  .subItems {
    margin-left: $spacing__component-inner--default;
  }
</style>
