        <template>
  <div class="product">
    <img :src="image" alt="" />
    <h1>
      {{ product }}
      <a :href="link" target="_blank">More products like this</a>
    </h1>
    <p v-if="inventory>10">instock</p>
    <p v-else-if="inventory <=10 && inventory >0">almost sold out</p>
    <p v-else>outstock</p>
   <ul>
       <li v-for="detail in details" :key="detail">{{ detail }}</li>
   <li v-for="size in sizes" :key="size">{{ size }}</li>
   </ul>
     <div v-for="variant in variants" :key="variant.variantId">
        <p>{{ variant.variantColor }}</p>
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
        variantColor: 'green'    
      },
      {
        variantId: 2235,
        variantColor: 'blue'
      }
    ],
    sizes: ['S', 'M', 'L', 'XL', 'XXL', 'XXXL'],
   
    };
  },
};


</script>
<style scoped>
body{
    display: flex;
    justify-content: center;
    text-align: center;
}
ul{
    text-decoration: none;
}

</style>
        