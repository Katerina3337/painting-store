<template>
  <div class="product">
    <v-carousel height="auto" :hide-delimiters="true" show-arrows="hover">
      <v-carousel-item
          :src="product.img"
          cover
      ></v-carousel-item>

      <v-carousel-item
          :src="product.img"
          cover
      ></v-carousel-item>

      <v-carousel-item
          :src="product.img"
          cover
      ></v-carousel-item>
    </v-carousel>
    <div class="product__wrapper">
      <div class="product__title">{{ product.name }}</div>
      <div class="product__info">{{ product.info }}</div>
      <div class="product__price">
        <div class="product__price--previous">{{ product.previousPrice }}</div>
        <div class="product__price--current">{{ product.currentPrice }}</div>
      </div>
    </div>


  </div>
</template>

<script>
export default {
  props: ['product'],
}
</script>

<style scoped>
.product {
  display: flex;
  flex-direction: column;
  justify-content: center;

  background-color: white;
}

.product__wrapper {
  padding: 45px;
}

.product__title {
  margin-bottom: 15px;
  font-size: 18px;
}

.product__info {
  margin-bottom: 15px;
  font-size: 15px;
}

.product__price {

}

.product__price--previous {
  font-weight: 300;
  font-size: 14px;
  line-height: 21px;
  color: #A0A0A0;
  text-decoration: line-through;
}

.product__price--current {
  font-weight: 700;
  font-size: 16px;
  line-height: 24px;
}
</style>