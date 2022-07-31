<template>
  <div id="app">
    <Layout>
      <template #top><h1 class="title">Добавление товара</h1></template>
      <template #bottom>
        <ProductForm @submit="addProduct" />
        <!-- products -->

      </template>
    </Layout>
  </div>
</template>

<script>
import Layout from './components/Layout.vue';
import ProductForm from './components/ProductForm.vue';
import { ref, computed, reactive } from 'vue';
const IMGAE_URL =
  'https://images.unsplash.com/photo-1526170375885-4d8ecf77b99f?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=640&q=80';
const genericItem = () => ({
  id: 'item:' + Math.floor(Math.random() * 100),
  name: 'Наименование товара ' + Math.floor(Math.random() * 100),
  desc: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
  image: IMGAE_URL,
  price: '10 000',
});
export default {
  name: 'App',
  components: {
    Layout,
    ProductForm,
  },
  setup() {
    const products = ref(Array.from({ length: 10 }, (_, idx) => genericItem()));
    // const filteredProducts = computed(()=> prdocuts);

    const addProduct = (data) => {
      // console.log(data);
      products.value.push(data);
    };
    const removeProduct = (data) => {};
    return {
      products,
      addProduct,
    };
  },
};
</script>

<!-- <style lang="scss"></style> -->
<style lang="scss" scoped>
@import 'assets/_base.scss';

#app {
}
.title {
  font-size: 1.75rem;
  white-space: nowrap;
}
</style>
