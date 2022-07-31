<template>
  <article
    class="product-card"
    tabindex="-1"
    @mouseover="isHover = true"
    @mouseleave="isHover = false"
  >
    <div class="cover">
      <img class="product-image" :src="i" loading="lazy" alt="Some product" />
    </div>
    <div class="contents">
      <h2 class="product-title">{{ title }}</h2>
      <p class="product-desc">{{ desc }}</p>
      <div class="product-value">{{ price }} <span>руб.</span></div>
    </div>
    <button v-show="isHover" class="btn del-product-btn" @click=""></button>
  </article>
</template>

<script>
import { ref } from 'vue';
export default {
  name: 'ProductCard',
  props: [],
  emits: [],
  components: {},
  setup() {},
};
</script>

<style lang="scss" scoped>
.product-card {
  display: flex;
  flex-direction: column;
  align-items: stretch;
  justify-content: stretch;
  min-width: 20rem;
  min-height: 26rem;
  cursor: pointer;
  border-radius: 0.25rem;
  position: relative;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
}
</style>
