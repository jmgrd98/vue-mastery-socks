<template>
  <div>
  <HeaderComponent/>

  <main>
  <h1>{{product}}</h1>

  <div class="product-summary">
    <img v-bind:src="image"/>

    <p>Lorem</p>

  </div>
  </main>

  </div>
</template>

<script>

import HeaderComponent from './components/Header'

export default {
  name: 'App',
  components: {
    HeaderComponent
  },
  data(){
    return {
      product: 'Socks',
      image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQMQAM-2DmaQkQAk4CHG_KagUFvO0j0JGAi0IiXKI_0oAe9TVZGnmp1DwmrYWeBUwdJZGU',

    }
  }
}
</script>

<style>
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  list-style: none;
  font-family: "Roboto Thin", sans-serif;
}

  main{
    padding: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;

  }

  .product-summary{
    margin-top: 50px;
    display: flex;
    align-items: center;
    justify-content: space-around;
    width: 50%;
  }

    img{
      border: 1px solid gray;
      padding: 10px;
    }


</style>
