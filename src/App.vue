<template>
  <div id="app">
    <Layout>
      <template #top>
        <h1 class="title">Добавление товара</h1>
        <ProductFilter />
      </template>
      <template #bottom>
        <ProductForm @submit="addProduct" />
        <Products :products="products" @remove-product="removeProduct" />
      </template>
    </Layout>
  </div>
</template>

<script>
import ProductFilter from './components/Filter.vue';
import Layout from './components/Layout.vue';
import ProductForm from './components/ProductForm.vue';
import Products from './components/Products.vue';
import { ref, computed, reactive } from 'vue';
const IMGAE_URL =
  'https://images.unsplash.com/photo-1526170375885-4d8ecf77b99f?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=640&q=80';
const genericItem = (idx) => ({
  id: 'item:' + Math.floor(Math.random() * 100),
  name: 'Наименование товара ' + (idx + 1),
  desc: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
  image: IMGAE_URL,
  price: '10 000',
});
export default {
  name: 'App',
  components: {
    Layout,
    ProductForm,
    Products,
    ProductFilter,
  },
  setup() {
    const filter = ref('');
    const products = ref(
      Array.from({ length: 10 }, (_, idx) => genericItem(idx))
    );
    // const filteredProducts = computed(()=> prdocuts);

    const addProduct = (data) => {
      // console.log(data);
      products.value.push(data);
    };
    const removeProduct = (id) => {
      console.log('remove', id);
      products.value = products.value.filter((item) => item.id !== id);
    };
    return {
      products,
      addProduct,
      removeProduct,
    };
  },
};
</script>

<style lang="scss" scoped>
@import './assets/_base.scss';

#app {
}
.title {
  font-size: 1.75rem;
  white-space: nowrap;
}
</style>
