<template>
  <div class="auth-form__wrapper">
    <form class="auth-form" @submit.prevent="onUserLogin">
      <div class="input__wrapper">
        <my-input
          v-model.trim="name"
          inputClass="auth-form__input"
          labelClass="auth-form__label"
          @focus="validationNameError = false"
          v-bind:class="{ error: validationNameError }"
          >Name</my-input
        >
        <!-- <label class="auth-form__label" for="name">Name</label>
        <input
          v-model.trim="name"
          class="auth-form__input"
          @focus="validationNameError = false"
          v-bind:class="{ error: validationNameError }"
          id="name"
          type="text"
          name="name"
        /> -->
        <p v-if="validationNameError" class="error__input-text">
          <img
            class="error-svg"
            :src="require('@/assets/images/Vector.svg')"
            alt="error logo"
            height="11"
            width="11"
          />
          Enter name
        </p>
      </div>
      <div class="input__wrapper">
        <my-input
          v-model.trim="password"
          inputClass="auth-form__input"
          labelClass="auth-form__label"
          v-bind:class="{ error: validationPasswordError }"
          @focus="validationPasswordError = false"
          id="password"
          type="password"
          name="password"
          >Password</my-input
        >
        <!-- <label class="auth-form__label" for="password">Password</label>
        <input
          v-model.trim="password"
          class="auth-form__input"
          v-bind:class="{ error: validationPasswordError }"
          @focus="validationPasswordError = false"
          id="password"
          type="password"
          name="password"
        /> -->
        <p v-if="validationPasswordError" class="error__input-text">
          <img
            class="error-svg"
            :src="require('@/assets/images/Vector.svg')"
            alt="error logo"
            height="11"
            width="11"
          />
          Enter password
        </p>
      </div>
      <my-button type="btn__login" text="LOGIN" />
      <my-button type="btn__forgot-password" text="Forgot Password" />
    </form>
    <my-button type="btn__register" fullWidth text="Register now" />
  </div>
</template>

<script>
import { mapMutations, mapGetters } from "vuex";
export default {
  data() {
    return {
      name: "",
      password: "",
      validationNameError: false,
      validationPasswordError: false,
    };
  },
  computed: {
    ...mapGetters({
      userLoginInfo: "userLoginInfo",
    }),
  },
  methods: {
    ...mapMutations({
      loginUser: "loginUser",
    }),
    async onUserLogin() {
      if (this.password === "" && this.name === "") {
        this.validationPasswordError = true;
        this.validationNameError = true;
        return;
      }

      if (this.name === "") {
        this.validationNameError = true;
        return;
      }

      if (this.password === "") {
        this.validationPasswordError = true;
        return;
      }

      await this.loginUser({ login: this.name, password: this.password });
      this.name = "";
      this.password = "";
      this.$router.push("/todo");
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/variables.scss";

.auth-form__wrapper {
  margin: 20px auto 0;

  background: $auth-form-background-color;
  box-shadow: 2px 2px 15px 2px rgba(0, 0, 0, 0.1);

  @media screen and (min-width: 768px) {
    width: 335px;
    margin: 0;
    position: absolute;
    right: -5px;
    bottom: 170px;
  }

  @media screen and (min-width: 1280px) {
    width: 480px;
    right: 0;
  }
}

.auth-form {
  display: flex;
  flex-direction: column;
  padding: 40px 30px 25px;
}

// .auth-form__label {
//   margin-bottom: 7px;

//   font-family: $main-font-family;
//   font-weight: 300;
//   font-size: 15px;
//   line-height: 10px;

//   color: $main-text-color;

//   @media screen and (min-width: 768px) {
//     font-size: 18px;
//     line-height: 21px;
//   }
// }
.input__wrapper {
  display: flex;
  flex-direction: column;
  margin-bottom: 40px;
}
// .auth-form__input {
//   height: 53px;
//   margin-bottom: 5px;
//   padding: 15px;

//   font-family: $main-font-family;
//   font-size: 18px;
//   line-height: 21px;

//   color: $main-text-color;
//   background: $auth-form-background-color;
//   border: 1px solid #9a9a9a;
// }
// .auth-form__input:hover,
// .auth-form__input:focus {
//   border-color: #101010;
// }
.error__input-text {
  font-family: $main-font-family;
  font-size: 16px;
  line-height: 19px;
  color: $error-input-border-text;
}
.error {
  border-color: $error-input-border-text;
}
</style>
