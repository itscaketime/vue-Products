<template>
  <div class="products">
    <ProductCard
      v-for="product in products"
      :key="product.id"
      :product="product"
      @remove-product=""
    />
  </div>
</template>

<script>
import ProductCard from './ProductCard.vue';
import { ref } from 'vue';
export default {
  name: 'Products',
  props: ['products'],
  emits:['remove-product']
  components: {
    ProductCard,
  },
  setup(props) {},
};
</script>

<style lang="scss" scoped>
.products {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1rem;
  margin-left: 21rem;
}
</style>
