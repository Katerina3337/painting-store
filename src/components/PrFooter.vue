<template>
  <footer class="footer">
    <div class="container">
      <pr-nav></pr-nav>
      <div class="contacts">
        <div class="contacts__phone">
          <img class="contacts__phone-img" src="./../assets/img/icons/phone.png" alt="phone">
          <span class="contacts__phone-text">+7 (812) 555-55-55</span>
        </div>
        <div class="contacts__location">
          <img class="contacts__location-img" src="./../assets/img/icons/location.png" alt="location">
          <span class="contacts__location-text">г. Санкт-Петербург, ул. Ефимова, 3</span>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
import PrNav from "@/components/PrNav.vue";

export default {
  components: {PrNav}
}
</script>

<style scoped>
.footer {
  width: 100%;

  background-color: #ECEAEA;
}
.container {
  max-width: 1300px;
  margin: 0px auto;
  padding: 37px;

  font-size: 14px;

  display: flex;
  justify-content: space-between;
  align-items: center;
}

.contacts {
  display: flex;
  margin-left: 127px;
}

.contacts__phone, .contacts__location {
  display: flex;
  align-items: center;
}

.contacts__phone {
  margin-right: 54px;
}

.contacts__phone-img {
  margin-right: 9px;
}

.contacts__location-img {
  margin-right: 10px;
}

@media (max-width: 1350px) {
  .contacts {
    margin: 0 auto;
  }
}

@media (max-width: 650px) {
  .contacts {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .contacts__phone {
    margin-bottom: 15px;
  }
}
</style>