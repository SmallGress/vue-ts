<style lang="scss" scoped>
.Item {
    $bc: rgb(222, 222, 222);

    list-style: none;
    min-height: 48px;
    background: #fff;
    box-shadow: 0 2px 3px $bc;

    border-bottom: 1px solid $bc;

    padding: 8px;

    position: relative;
    z-index: 9;

    &.first {
        border-top: 1px solid rgb(230, 230, 230);

        .corner {
            display: none;
        }
    }


    .corner {
        $size: 24px;

        width: $size;
        height: $size;

        position: absolute;
        z-index: 10;
        border-radius: 50%;

        &.corner-left {
            background: #fff;
            box-shadow: inset -2px 0px 1px $bc;
            top: $size / -2;
            left: $size / -2;
        }

        &.corner-right {
            $halfSize:  $size / 2;
            background: #fff;
            box-shadow: inset 2px 0px 1px $bc;
            top: $halfSize * -1;
            left: calc(100% - #{$halfSize} );
        }
    }
}
</style>

<template>
  <li class="Item" v-bind:class="{first: isFirst}">
      <slot></slot>
      <div class="corner corner-left"></div>
      <div class="corner corner-right"></div>
  </li>
</template>

<script lang="ts">
export default {
  name: "Item",
  data() {
      return {}
  },
  props: ["isFirst"]
}
</script>
