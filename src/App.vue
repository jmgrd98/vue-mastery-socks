<template>
  <div>
    <HeaderComponent/>

    <main>
      <h1>{{ title }}</h1>

      <ProductComponent :premium="premium" @add-to-cart="updateCart"/>
      <ProductComponent @add-to-cart="updateCart"/>

      <span>Cart: {{ cart.length }}</span>

      <ReviewFormComponent @review-submitted="addReview"/>
    </main>
  </div>
</template>

<script>

import HeaderComponent from './components/Header';
import ProductComponent from './components/Product'
import ReviewFormComponent from './components/ReviewForm'

export default {
  name: 'App',
  title: '',
  components: {
    HeaderComponent,
    ProductComponent,
    ReviewFormComponent
  },
  data() {
    return {
      cart: [],
      brand: 'Vue Mastery',
      product: 'Socks',
      premium: true,
    }
  },
  methods: {
    updateCart(id) {
      this.cart.push(id);
    }
  },
  computed: {
    title() {
      return this.brand + ' ' + this.product
    }
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  list-style: none;
  font-family: "Roboto Thin", sans-serif;
}

main {
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;

}


span {
  background-color: dodgerblue;
  padding: 10px;
  width: 100px;
  position: absolute;
  right: 20px;
  top: 70px;
  border-radius: 10px;
  background-color: #d8d8d8;
}


</style>
