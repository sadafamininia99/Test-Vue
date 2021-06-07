        <template>
  <div class="product">
    <img :src="image" alt="" width="400" />
    <h1>
      {{ product }}
      <a :href="link" target="_blank">More products like this</a>
    </h1>
    <p v-if="inventory > 10">instock</p>
    <p v-else-if="inventory <= 10 && inventory > 0">almost sold out</p>
    <p v-else>outstock</p>
    <ul>
      <li v-for="detail in details" :key="detail">{{ detail }}</li>
      <li v-for="size in sizes" :key="size">{{ size }}</li>
    </ul>
    
    <div v-for="variant in variants" 
    :key="variant.variantId"
    class="color-box"
    :style="{ backgroundColor: variant.variantColor } "
      @mouseover="updateProduct(variant.variantImage)">
    </div>

    <button v-on:click="addToCart">Add to cart</button>

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
      image:
        "https://www.vuemastery.com/images/challenges/vmSocks-green-onWhite.jpg",
      link:
        "https://www.amazon.com/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=socks",
        inventory :8,
        details: ['80% cotton', '20% polyester', 'Gender-neutral'],
    
     variants: [
      {
        variantId: 2234,
        variantColor: 'green',
        variantImage: 'https://www.vuemastery.com/images/challenges/vmSocks-green-onWhite.jpg'
      },
      {
        variantId: 2235,
        variantColor: 'blue',
        variantImage: 'https://www.vuemastery.com/images/challenges/vmSocks-blue-onWhite.jpg'
      }
     ], 
     cart :0
    }
    
    },
    methods:{
        addToCart:function()
        {
           this.cart += 1
        }
    },
      updateProduct(variantImage) {
      this.image = variantImage
    }
  }
  

    



</script>
<style scoped>
button {
  margin-top: 50px;
  border: none;
  background-color: #09c422;
    box-shadow: 0px .5px 1px #d8d8d8;
  color: white;
  height: 60px;
  width: 100px;
  font-size: 24px;
} 
.cart {
  margin-right: 25px;
  float: right;
  border: 1px solid #d8d8d8;
  padding: 5px 20px;
}
img{
  border: 3px solid #055a2b;
  width: 30%;
  margin: 40px;
  box-shadow: 0px .5px 1px #d8d8d8;

}
.color-box{
  width: 40px;
  height: 40px;
  margin-top: 5px;
}

</style>
        