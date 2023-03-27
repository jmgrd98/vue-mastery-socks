<template>
  <div>
    <HeaderComponent/>

    <main>
      <h1>{{ title }}</h1>

      <ProductComponent :premium="premium"/>
      <ProductComponent/>

      <span>Cart: {{ cart }}</span>

    </main>
  </div>
</template>

<script>

import HeaderComponent from './components/Header';
import ProductComponent from './components/Product'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    ProductComponent,
  },
  data() {
    return {
      cart: 0,
      premium: true,
    }
  },
  methods: {

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
