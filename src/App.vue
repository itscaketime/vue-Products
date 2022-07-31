<template>
  <div id="app">
    <Layout>
      <template #top><h1 class="title">Добавление товара</h1></template>
      <template #bottom>
        <!-- form -->
        <!-- products -->
      </template>
    </Layout>
  </div>
</template>

<script>
import Layout from './components/Layout.vue';
import { ref } from 'vue';
export default {
  name: 'App',
  components: {
    Layout,
  },
  setup() {},
};
</script>

<!-- <style lang="scss"></style> -->
<style lang="scss" scoped>
@import 'assets/_base.scss';

#app {
}
</style>
