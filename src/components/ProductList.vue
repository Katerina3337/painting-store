<template>
  <div class="container">
    <div class="product__title">Картины эпохи Возрождения</div>
    <div class="product__list">
      <product-item
          v-for="product in filteredProducts"
          :key="product.id"
          :product="product"
          @open-modal="openModal"
          @buy-product="handleBuyProduct"
      />
    </div>

      <div class="text-center">
        <v-dialog
            v-model="dialog"
            width="501"
        >
          <product-details :product="productDetails" />
        </v-dialog>
      </div>

  </div>
</template>

<script>
import ProductItem from "@/components/ProductItem.vue";
import ProductDetails from "@/components/ProductDetails.vue";
import productData from "@/data"
export default {
  components: {ProductDetails, ProductItem},
  props: ['search'],
  data() {
    return {
      dialog: false,
      productId: null,
      products: null,
    }
  },
  mounted() {
    const jsonLsProducts = localStorage.getItem('products')
    if(jsonLsProducts){
      this.products = JSON.parse(jsonLsProducts);
    }else{
      this.products = productData;
    }
  },
  computed: {
    filteredProducts() {
      if(!this.products) return []
      return this.products.filter(product => {
        if(!this.search) return true;
        return product.name.toLowerCase().includes(this.search);
      })
    },
    productDetails() {
      if(!this.productId) return null;
      return this.products.find(product => this.productId === product.id)
    }
  },
  methods: {
    openModal(id){
      this.productId = id;
      this.dialog = true;
    },
    saveProducts(){
      localStorage.setItem('products', JSON.stringify(this.products));
    },
    handleBuyProduct(id){
      const product = this.products.find(product => id === product.id);
      product.status = 'pending';
      setTimeout(() => {
        product.status = 'in_basket';
        this.saveProducts();
      }, 2000);
    }
  }
}

</script>

<style scoped>
.container {
  max-width: 1216px;
  margin: 45px auto 0;
}

.product__title {
  font-weight: 700;
  font-size: 24px;
  line-height: 36px;
  margin-bottom: 39px;
}

.product__list {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  margin-bottom: 320px;
}

@media (max-width: 1350px) {
  .container {
    max-width: 1000px;
  }

  .product__title {
    text-align: center;
  }

  .product__list {
    padding: 20px;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    column-gap: 30px;
    row-gap: 30px;
  }
}
</style>