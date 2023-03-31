<template>
  <header class="header">
    <div class="container">
      <pr-nav />
      <nav-mobile />
      <div class="search">
        <input @input="$emit('search-input', $event)" type="text" class="search__input" placeholder="Поиск по названию картины">
        <div class="search__button">Найти</div>
      </div>
    </div>
  </header>
</template>

<script>
import PrNav from "@/components/PrNav.vue";
import NavMobile from "@/components/NavMobile.vue";
export default {
  components: {PrNav, NavMobile},
  data(){
    return {
      enteredText: "",
    }
  }
}
</script>

<style scoped>
.header {
  width: 100%;

  border-bottom: 1px solid #E1E1E1;
}
.container {
  max-width: 1060px;
  margin: 24px auto;

  font-size: 14px;

  display: flex;
  justify-content: space-between;
  align-items: center;

}

.search {
  display: flex;
  align-items: center;
}

.search__input {
  font-family: 'Merriweather', sans-serif;
  font-size: 14px;
  width: 294px;
  padding: 13px 60px 14px 16px;
  color: #9F9F9F;
  border: 1px solid #E1E1E1;
  outline: 0;
}

.search__button {
  padding: 14px 36px 15px 36px;
  color: #FFFFFF;
  background-color: #403432;
}

@media (max-width: 1350px) {
  .container {
    justify-content: center;
  }
}

@media (max-width: 650px) {
  .search__input {
    width: 250px;
    padding: 13px 45px 14px 16px;
  }
}

@media (max-width: 430px) {
  .search__input {
    width: 200px;
  }
  .search__button {
    padding: 14px 30px 15px 30px;
  }
}

@media (max-width: 370px) {
  .search__button {
    padding: 14px 25px 15px 25px;
  }
}

@media (max-width: 330px) {
  .search__input {
    width: 170px;
  }
  .search__button {
    padding: 14px 15px 15px 15px;
  }
}
</style>