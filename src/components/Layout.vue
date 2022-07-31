<template>
  <div class="top"><slot name="top"></slot></div>
  <div class="bottom"><slot name="bottom"></slot></div>
</template>

<script>
import { ref } from 'vue';
export default {
  name: 'Layout',
  setup() {},
};
</script>

<style lang="scss" scoped>
.top {
}
.bottom {
}
</style>
