<template>
  <section class="main">
    <div class="container">
      <h1 class="heading">
        Welcome to <br />
        Business Analytics Online
      </h1>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import "@/assets/variables.scss";

.main {
  background-image: url("@/assets/images/Фон-1x.jpg");
  background-position: center;
  background-size: cover;
}

.heading {
  font-family: $main-font-family;
  font-style: normal;
  font-weight: 400;
  padding-top: 30px;
  padding-bottom: 30px;

  font-size: 20px;
  line-height: 35px;
  text-align: right;

  color: $main-header-color;

  @media screen and (min-width: 480px) {
    padding-top: 35px;
    padding-bottom: 35px;

    font-size: 25px;
    line-height: 40px;
  }
  @media screen and (min-width: 768px) {
    padding-top: 80px;
    padding-bottom: 80px;

    font-size: 30px;
    line-height: 44px;
    text-align: left;
  }

  @media screen and (min-width: 1280px) {
    padding-top: 215px;
    padding-bottom: 70px;

    font-size: 55px;
    line-height: 86px;
  }
}
</style>
