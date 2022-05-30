<template>
  <div class="email-signin">
    <form action="">
      <span class="email-wrapper">
        <label for="email">Email</label>
        <input
          type="email"
          name="email"
          id="email"
          placeholder="Email address"
          v-model="emailInput"
        />
      </span>
      <span class="password-wrapper">
        <label for="password">Password</label>
        <input
          :type="showPassword ? 'text' : 'password'"
          name="password"
          id="password"
          placeholder="Password"
          v-model="passwordInput"
          @focus="showToggle = true"
        />
        <span class="toggle-pass-container">
          <img
            src="..\assets\eye.png"
            alt=""
            v-if="showToggle && !showPassword"
            @click="showPassword = true"
          />
          <img
            src="..\assets\eye-slash.png"
            alt=""
            v-if="showToggle && showPassword"
            @click="showPassword = false"
          />
        </span>
        <input
          v-if="pageType === 'join'"
          type="sec-password"
          name="sec-password"
          id="sec-password"
          placeholder="Re-enter password"
          v-model="secPasswordInput"
        />
      </span>
      <span class="forgot-pass">
        <a href="">Forgotten password?</a>
      </span>
      <button :disabled="submitDisabled ? true : false">sign-in</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "EmailSignIn",
  props: {
    pageType: String,
  },
  data() {
    return {
      emailInput: "",
      emailValid: false,
      passwordInput: "",
      passwordValid: false,
      secPasswordInput: "",
      secPasswordValid: false,
      submitDisabled: true,

      showToggle: false,
      showPassword: false,
    };
  },
  watch: {
    emailInput() {
      if (this.validateEmail(this.emailInput)) {
        this.emailValid = true;
      } else {
        this.emailValid = false;
      }
    },
    passwordInput() {
      if (this.validatePassword(this.passwordInput)) {
        this.passwordValid = true;
      } else {
        this.passwordValid = false;
      }
    },
    secPasswordInput() {
      if (this.validatePassword(this.secPasswordInput)) {
        this.secPasswordValid = true;
      } else {
        this.secPasswordValid = false;
      }
    },
    emailValid() {
      this.enableButton();
    },
    passwordValid() {
      this.enableButton();
    },
    secPasswordValid() {
      this.enableButton();
    },
  },
  methods: {
    validateEmail(email) {
      const regex =
        /^([a-zA-Z0-9_.+-])+@(([a-zA-Z0-9-])+.)+([a-zA-Z0-9]{2,6})+$/;
      return regex.test(email);
    },
    validatePassword(password) {
      // upper & lower case, special char, min 6
      const regex = /^(?=.*[A-Z])(?=.*[#$@!%&*?])[A-Za-zd#$@!%&*?]{6,}/;
      return regex.test(password);
    },
    enableButton() {
      if (this.pageType === "signin") {
        if (this.emailValid && this.passwordValid) {
          this.submitDisabled = false;
        } else {
          this.submitDisabled = true;
        }
      } else {
        if (this.emailValid && this.passwordValid && this.secPasswordValid) {
          this.submitDisabled = false;
        } else {
          this.submitDisabled = true;
        }
      }
    },
  },
};
</script>

<style scoped>
.email-signin {
  background-color: #fff;
  width: 590px;
  height: auto;
  margin: auto;
  margin-top: 33px;
  border-radius: 9px;
  padding: 30px;
  box-sizing: border-box;
}
form {
  font-size: 0.875rem;
  text-align: left;
}
input {
  width: 100%;
  height: 40px;
  box-sizing: border-box;
  padding-left: 18px;
  border: 1px solid #959595;
  border-radius: 4px;
  margin-top: 8px;
  transition: 0.2s ease-in;
}
.email-wrapper input {
  margin-bottom: 15px;
}
input:hover {
  border: 4px solid #171717;
  padding-left: 15px;
}

.password-wrapper {
  display: flex;
  flex-wrap: wrap;
}
.toggle-pass-container {
  margin-top: -28px;
  position: relative;
  left: 490px;
}
.toggle-pass-container img {
  z-index: 10;
}

.forgot-pass {
  margin-top: 36px;
  display: block;
  text-align: center;
  font-size: 0.75rem;
}
a {
  color: #171717;
}

button {
  width: 165px;
  height: 45px;
  background-color: #3843f1;
  color: #fff;
  border: none;
  outline: none;
  border-radius: 6px;
  display: block;
  margin: auto;
  margin-top: 20px;
  font-size: 1rem;
  font-weight: 600;
  transition: 0.1s ease-in;
}
button:hover {
  background-color: #28348a;
  cursor: pointer;
}
button:disabled {
  background-color: #eeeeee;
}
button:disabled:hover {
  background-color: #eeeeee;
  cursor: default;
}
</style>
