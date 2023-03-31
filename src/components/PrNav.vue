<template>
  <nav class="nav">
    <ul class="nav__list">
      <li class="nav__item"><a href="#" class="nav__link">Каталог</a></li>
      <li class="nav__item"><a href="#" class="nav__link">Доставка</a></li>
      <li class="nav__item"><a href="#" class="nav__link">Оплата</a></li>
      <li class="nav__item"><a href="#" class="nav__link">Контакты</a></li>
      <li class="nav__item"><a href="#" class="nav__link">О компании</a></li>
    </ul>
  </nav>
</template>

<style scoped>
.nav__list {
  display: flex;
  column-gap: 48px;
  list-style: none;
  color: #343030;
}

@media (max-width: 1350px){
  .nav__list {
    display: none;
  }
}
</style>