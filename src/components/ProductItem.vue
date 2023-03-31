<template>
  <div class="product" :class="{'product--sold': product.status === 'sold_out'}">
    <img @click="$emit('open-modal', product.id)" :src="product.img" alt="" class="product__img">
    <div class="picture__description">
      <div @click="$emit('open-modal', product.id)" class="product__title">{{ product.name }}</div>
      <div v-if="product.status !== 'sold_out'" class="product__info">
        <div class="product__price">
          <div class="product__price--previous">{{ product.previousPrice }}</div>
          <div class="product__price--current">{{ product.currentPrice }}</div>
        </div>
        <button @click="$emit('buy-product', product.id)" class="button--buy" :class="btnCssClass">
          <v-progress-circular v-if="product.status === 'pending'" :size="15" width="3" indeterminate></v-progress-circular>
          <v-icon v-if="product.status === 'in_basket'"  icon="mdi-check" />
          {{ btnText }}
        </button>
      </div>
      <p v-else class="sold--title">Продана на аукционе</p>

    </div>
  </div>
</template>

<script>
export default {
  props: ['product'],
  data() {
    return {
      isLoading: null,
      isAdded: null,
    }
  },
  computed: {
    btnCssClass(){
      switch(this.product.status){
        case 'available'  : return 'button--available';
        case 'pending'    : return 'button--pending';
        case 'in_basket'  : return 'button--basket';
        case 'sold_out'   : return 'button--sold-out'
      }
      return ''
    },
    btnText(){
      switch(this.product.status){
        case 'available'  : return 'Купить';
        case 'pending'    : return 'Ожидание...';
        case 'in_basket'  : return 'В корзине';
      }
      return ''
    }
  },
}
</script>

<style scoped>
.product {
  max-width: 280px;
  padding-bottom: 26px;
  display: flex;
  flex-direction: column;
  border: 1px solid #E1E1E1;
}

.product__img {
  width: 280px;
  height: 180px;
  background-color: blueviolet;
  cursor: pointer;
}

.product__title {
  margin: 20px 36px 22px 24px;
  font-weight: 400;
  font-size: 18px;
  line-height: 27px;
  cursor: pointer;
}

.product__info {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0 24px;
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

.button--buy {
  width: 112px;
  height: 48px;
  font-family: 'Merriweather', sans-serif;
  font-weight: 700;
  font-size: 14px;
  line-height: 21px;
  text-align: center;
  color: #F4F6F9;
  background-color: #382E2B;
  border: none;
}

.button--pending, .button--basket {
  width: 118px;
}

.product--sold {
  opacity: 0.5;
}

.sold--title {
  margin-left: 24px;
  margin-top: 34px;
  font-weight: 700;
  font-size: 16px;
  line-height: 24px;
  color: #343030;
}
</style>