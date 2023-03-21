<template>
  <div>

    <main>

      <div class="product-summary">
        <img v-bind:src="image" alt="Green Socks"/>

        <div class="product-description">
          <h2 v-if="inStock">In Stock</h2>
          <h2 v-else>Out of Stock</h2>

          <ul>
            <li v-for="detail in details" :key="detail">{{ detail }}</li>
          </ul>

          <ul class="colors">
            <li
                v-for="(variant, index) in variants"
                :key="variant.id"
                @mouseover="updateVariant(index)"
                class="color-circle"
                :style="{backgroundColor: variant.color}">
            </li>
          </ul>
        </div>

        <button class="button" v-on:click="addToCart" :disabled="!inStock" :class="{disabledBtn: !inStock}">Add to
          Cart
        </button>
        <span>Cart: {{ cart }}</span>

      </div>
    </main>

  </div>
</template>

<script>

export default {
  name: 'ProductComponent',
  components: {

  },
  data() {
    return {
      brand: 'Vue Mastery',
      product: 'Socks',
      cart: 0,
      selectedVariant: 0,
      details: ['50% cotton', '30% wool', '20% polyester'],
      variants: [
        {
          id: 2234,
          color: 'green',
          image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQMQAM-2DmaQkQAk4CHG_KagUFvO0j0JGAi0IiXKI_0oAe9TVZGnmp1DwmrYWeBUwdJZGU',
          quantity: 50,
        },
        {
          id: 2235,
          color: 'blue',
          image: 'data:image/jpeg;base64,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',
          quantity: 0,
        },
      ]
    }
  },
  methods: {
    addToCart() {
      this.cart++;
    },
    updateImage(variantImage) {
      this.image = variantImage
    },
    updateVariant(index) {
      this.selectedVariant = index;
    }
  },
  computed: {
    title() {
      return this.brand + ' ' + this.product;
    },
    image() {
      return this.variants[this.selectedVariant].image;
    },
    inStock() {
      return this.variants[this.selectedVariant].quantity;
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

.colors {
  display: flex;
  gap: 5px;
}

.color-circle {
  width: 50px;
  height: 50px;
  margin-top: 8px;
  border: 2px solid #d8d8d8;
  border-radius: 50%;
}

.product-summary {
  margin-top: 50px;
  display: flex;
  align-items: center;
  justify-content: space-around;
  width: 50%;
}

.product-description {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

img {
  border: 1px solid gray;
  padding: 10px;
}

button {
  padding: 10px;
  color: white;
  background-color: olive;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.disabledBtn {
  background-color: #d8d8d8;
  cursor: not-allowed;
}

span {
  background-color: dodgerblue;
  padding: 10px;
}


</style>