<template>
  <div id="app" class="container mt-5">
    <h1>IDShop</h1>
    <!-- Penamaan yang sesuai -->
    <price-slider :sliderStatus="sliderStatus" :maximum.sync="maximum" ></price-slider>
    <ProductList :products="products" :maximum="maximum" @add="addItem"></ProductList>
  </div>
</template>

<script>
import PriceSlider from "./components/PriceSlider.vue";
import ProductList from "./components/ProductList.vue";

export default {
  name: "App",
  data() {
    return {
      maximum: 50,
      products: [],
      cart:[],
      sliderStatus: true

    };
  },
  components: {
    PriceSlider,
    ProductList
  },
  mounted() {
    fetch("https://hplussport.com/api/products/order/price")
      .then((response) => response.json())
      .then((data) => {
        this.products = data;
      });
  },
  methods:{
    //   menambahkan product to cart
    addItem: function(product) {
        var productIndex;
        var productExist = this.cart.filter(function (item, index) {
            if (item.product.id == Number(product.id)) {
                productIndex = index;
                return true;
            } else {
                return false;
            }
        });
        if (productExist.length) {
            this.cart[productIndex].qty++;
        } else {
            this.cart.push({product: product, qty: 1})
        }
      },
  }
};
</script>
<!-- membersihkan format lint -->
<!-- npm run lint -- --fix -->