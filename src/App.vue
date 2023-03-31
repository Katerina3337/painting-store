<template>
  <pr-header @search-input="updateSearch"></pr-header>
  <product-list :search="searchString"></product-list>
  <pr-footer></pr-footer>
</template>

<script>
import PrHeader from "@/components/PrHeader.vue";
import ProductList from "@/components/ProductList.vue";
import PrFooter from "@/components/PrFooter.vue";

export default {
  components: {ProductList, PrHeader, PrFooter},
  data(){
    return {
      searchString: '',
    }
  },
  methods: {
    updateSearch(e) {
      this.searchString = e.target.value.toLowerCase();
    }
  }
}
</script>




<style scoped>

</style>
