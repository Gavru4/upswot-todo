<template>
  <section class="header">
    <div class="header__top-wrapper"></div>
    <div class="header__logo-wrapper">
      <div class="container">
        <img
          class="logo"
          :src="require('@/assets/images/logo.png')"
          alt="my-logo"
        />
      </div>
    </div>
  </section>
</template>

<script>
import Container from "@/assets/Container.vue";

export default {
  components: {
    Container,
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/variables.scss";

.header__top-wrapper {
  height: 53px;
  width: 100vw;
  background-color: $header-top-bgc;
}

.header__logo-wrapper {
  width: 100vw;
  padding: 15px 0;

  background: linear-gradient(
    180deg,
    $header-gradient-top-bgc,
    $header-gradient-bottom-bgc
  );
}

.logo {
  display: block;
  height: 50px;
  width: 80px;
  margin: 0 auto;

  @media screen and (min-width: 480px) {
    height: 66px;
    width: 103px;
  }

  @media screen and (min-width: 768px) {
    height: 66px;
    width: 103px;
    margin: 0;
  }

  @media screen and (min-width: 1280px) {
    height: 66px;
    width: 103px;
  }
}
</style>
