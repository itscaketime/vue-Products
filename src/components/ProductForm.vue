<template>
  <form method="POST" id="product-form" @submit.prevent="onFormSubmit">
    <div class="form-field">
      <label for="input-text"
        ><span class="required">Наименование товара</span></label
      >
      <input
        type="text"
        id="input-text"
        name="text"
        placeholder="Введите наименование товара"
        v-model="productName"
      />
    </div>
    <div class="form-field">
      <label for="input-desc">Описание товара</label>
      <textarea
        maxlength="100"
        type="desc"
        id="input-desc"
        name="desc"
        placeholder="Введите описание товара"
        v-model="productDesc"
      >
      </textarea>
    </div>
    <div class="form-field">
      <label for="input-value"
        ><span class="required"
          >Введите ссылку на изображение товара</span
        ></label
      >
      <input
        type="text"
        id="input-image"
        name="image"
        placeholder="Введите ссылку"
        v-model="productImage"
      />
    </div>
    <div class="form-field">
      <label for="input-value"><span class="required">Цена товара</span></label>
      <input
        type="text"
        id="input-value"
        name="value"
        placeholder="Введите цену"
        v-model="productPrice"
      />
    </div>
    <button class="add-btn" type="submit">Добавить товар</button>
  </form>
</template>

<script>
import useValidation from '../use/useValidation';
import { ref } from 'vue';
export default {
  name: 'ProductForm',
  components: {},
  emits: ['submit'],
  setup(props, ctx) {
    const productName = ref('');
    const productDesc = ref('');
    const productImage = ref('');
    const productPrice = ref('');

    const productNameValidated = useValidation(
      /[A-Za-zЁёА-я0-9]/mu,
      productName
    );
    const onFormSubmit = (ev) => {
      console.log('form submit');
      let item = ctx.emit('submit', {
        id: 'item:' + Math.random() * 100,
        name: productName.value,
        desc: productDesc.value,
        image: productImage.value,
        price: productPrice.value,
      });
    };
    return {
      productName,
      productDesc,
      productImage,
      productPrice,
      onFormSubmit,
      productNameValidated,
    };
  },
};
</script>

<style lang="scss" scoped>
#product-form {
  background-color: white;
  z-index: 1000;
  width: 20rem;
  display: block;
  padding: 1.5rem;
  border-radius: 0.5rem;
  position: fixed;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
  .form-field {
    margin-bottom: 1rem;
    &:last-child {
      margin-bottom: none;
    }
  }
  .required {
    position: relative;
    &::after {
      content: '';
      width: 4px;
      height: 4px;
      display: block;
      border-radius: 100%;
      background-color: crimson;
      position: absolute;
      right: -4px;
      top: -2px;
    }
  }
  .add-btn {
    width: 100%;
  }
  .err {
  }
}
</style>
