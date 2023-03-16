<template>
  <div>
  <HeaderComponent/>

  <main>
  <h1>{{product}}</h1>

  <div class="product-summary">
    <img v-bind:src="image" alt="Green Socks"/>

    <div class="product-description">
    <h2 v-if="inStock">In Stock</h2>
    <h2 v-else>Out of Stock</h2>

      <ul>
        <li v-for="detail in details" :key="detail">{{detail}}</li>
      </ul>

      <ul>
        <li v-for="variant in variants" :key="variant.id">{{variant.color}}</li>
      </ul>
    </div>

    <button class="button" v-on:click="cart++">Add to Cart</button>
    <span>{{cart}}</span>

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
      inStock: true,
      cart: 0,
      details: ['50% cotton', '30% wool', '20% polyester'],
      variants: [
        {id: 2234, color: 'green'},
        {id: 2235, color: 'blue'},
      ]
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

  .product-description{
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

    img{
      border: 1px solid gray;
      padding: 10px;
    }

    button{
      padding: 10px;
      color: white;
      background-color: olive;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }


</style>
