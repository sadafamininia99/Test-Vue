<template>

  <div class="navbar">
    <h1>{{ product }}</h1>
    <p v-if="inStock">In Stock</p>
    <p v-else :class="{ outOfStock: !inStock }">Out of Stock</p>
    
    <div class="product-image">
      <img :src="image" width="400px" height="200px"/>
    </div>

       <div class="product-info">
      <h1>{{ title }}</h1>
      <p v-if="inStock">In Stock</p>
      <p v-else>Out of Stock</p>
      <p>{{ sale }}</p>
       </div>

    <ul>
      <li v-for="detail in details" :key="detail">{{ detail }}</li>
    </ul>

    <div
      class="color-box"
      v-for="variant in variants"
      :key="variant.variantId"
      :style="{ backgroundColor: variant.variantColor }"
      @mouseover="updateProduct(variant.variantImage)"
    ></div>

    <button
      v-on:click="addToCart"
      :disabled="!inStock"
      :class="{ disabledButton: !inStock }"
    >
      Add to cart
    </button>

    <div class="cart">
        <p>Cart({{ cart }})</p>
      </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      product: "Socks",
      brand: "vue masterful",
      selectedVariant: 0,
      details: ["80% cotton", "20% polyester", "Gender-neutral"],
      variants: [
        {
          variantId: 2234,
          variantColor: "green",
          variantQuantity: 10,
          variantImage:
            "https://www.vuemastery.com/images/challenges/vmSocks-green-onWhite.jpg",
        },
        {
          variantId: 2235,
          variantColor: "blue",
          variantQuantity: 0,
          variantImage:
            "https://www.vuemastery.com/images/challenges/vmSocks-blue-onWhite.jpg",
        },
      ],
      cart: 0,
      onsale: true,
    };
  },
  methods: {
    addToCart: function() {
      this.cart += 1;
    },
    updateProduct(index) {
      this.selectedVariant = index;
    },
  },

  computed: {
    title() {
      return this.brand + " " + this.product;
    },
    image() {
      return this.variants[this.selectedVariant].variantImage;
    },
    inStock() {
      // return this.variants[this.selectedVariant].variantQuantity;
      return this.variants[this.selectedVariant].variantQuantity;
    },
    sale() {
      if (this.onSale) {
        return this.brand + " " + this.product + " are on sale!";
      }
      return this.brand + " " + this.product + " are not on sale";
    },
  },
};
</script>
<style scoped>
body {
  font-family: tahoma;
  color: #282828;
  margin: 0px;
}

.nav-bar {
  background: linear-gradient(-90deg, #84cf6a, #16c0b0);
  height: 60px;
  margin-bottom: 15px;
}

#app {
  display: flex;
}

img {
  border: 1px solid #d8d8d8;
  width: 70%;
  margin: 40px;
  box-shadow: 0px 0.5px 1px #d8d8d8;
}

.product-image {
  flex-basis: 700px;
}

.product-info {
  margin-top: 10px;
  flex-basis: 500px;
}

.color-box {
  width: 40px;
  height: 40px;
  margin-top: 5px;
}

.cart {
  margin-right: 25px;
  float: right;
  border: 1px solid #d8d8d8;
  padding: 5px 20px;
}

button {
  margin-top: 30px;
  border: none;
  background-color: #1e95ea;
  color: white;
  height: 40px;
  width: 100px;
  font-size: 14px;
}

.disabledButton {
  background-color: #d8d8d8;
}

.review-form {
  width: 30%;
  padding: 20px;
  border: 1px solid #d8d8d8;
}

input {
  width: 100%;
  height: 25px;
  margin-bottom: 20px;
}

textarea {
  width: 100%;
  height: 60px;
}

.outOfStock {
  text-decoration: line-through;
}
</style>
