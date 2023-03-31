<template>
  <div class="navigation-mobile">
    <button class="navigation-mobile__burger" :class="{'navigation-mobile_burger--opened': showMenu}" @click="showMenu = !showMenu">
      <span></span>
      <span></span>
      <span></span>
    </button>
    <nav v-if="showMenu" class="nav">
      <ul class="nav__list">
        <li class="nav__item"><a href="#" class="nav__link">Каталог</a></li>
        <li class="nav__item"><a href="#" class="nav__link">Доставка</a></li>
        <li class="nav__item"><a href="#" class="nav__link">Оплата</a></li>
        <li class="nav__item"><a href="#" class="nav__link">Контакты</a></li>
        <li class="nav__item"><a href="#" class="nav__link">О компании</a></li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showMenu: false,
    }
  }
}

</script>

<style scoped>
.navigation-mobile {
  display: none;
  margin-right: 30px;
}
.nav {
  position: absolute;
  top: 50px;
  background: white;
  padding: 10px;
  z-index: 1;
  border: 2px solid #382E2B;
  width: 200px;
}

.nav__list {
  display: flex;
  column-gap: 48px;
  list-style: none;
  color: #343030;
  flex-direction: column;
}

.nav__item {
  padding: 14px;
  cursor: pointer;
}

.nav__item:hover {
  background: #382E2B;
  color: white;
}

.navigation-mobile__burger {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.navigation-mobile__burger span {
  width: 16px;
  height: 2px;
  border-radius: 2px;
  margin-bottom: 1px;
  background: #382E2B;
  transition: .4s all;
}

.navigation-mobile_burger--opened span:nth-child(1){
  transform: rotate(45deg) translateY(2px);
}

.navigation-mobile_burger--opened span:nth-child(2){
  display: none;
}

.navigation-mobile_burger--opened span:nth-child(3){
  transform: rotate(-45deg) translateY(-2px);
}

@media (max-width: 1350px){
  .navigation-mobile {
    display: block;
  }
}

@media (max-width: 370px) {
  .navigation-mobile{
    margin-right: 15px;
  }
}
</style>