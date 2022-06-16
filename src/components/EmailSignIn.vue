<template>
  <div class="email-signin">
    <form action="">
      <span class="forgot-pass">
        <a href="">Forgotten password?</a>
      </span>
      <span class="email-wrapper">
        <label for="email">Email</label>
        <input
          type="email"
          name="email"
          id="email"
          placeholder="Email address"
          v-model="emailInput"
          @blur="checkEmail"
        />
        <p id="invalid-email-msg" v-if="emailInvalidMsg">
          {{ emailInvalidMsg }}
        </p>
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
          @blur="checkPassword"
        />
        <p
          id="pass-requirements"
          :style="passwordInvalid ? { color: '#fa0521' } : { color: '#9f9f9f' }"
        >
          Must contain at least 1 uppercase letter and a special character
        </p>
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
          v-if="pageType === 'sign up'"
          :type="showSecPassword ? 'text' : 'password'"
          name="sec-password"
          id="sec-password"
          placeholder="Re-enter password"
          v-model="secPasswordInput"
          @focus="showSecToggle = true"
          @blur="checkSecPassword"
        />
        <span class="toggle-sec-pass-container">
          <img
            src="..\assets\eye.png"
            alt=""
            v-if="showSecToggle && !showSecPassword"
            @click="showSecPassword = true"
          />
          <img
            src="..\assets\eye-slash.png"
            alt=""
            v-if="showSecToggle && showSecPassword"
            @click="showSecPassword = false"
          />
        </span>
        <p id="invalid-pass-msg" v-if="passwordInvalidMsg">
          {{ passwordInvalidMsg }}
        </p>
      </span>

      <button :disabled="submitDisabled ? true : false">Continue</button>
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
      emailInvalidMsg: "",

      passwordInput: "",
      passwordValid: false,
      passwordInvalid: false,
      passwordInvalidMsg: "",

      secPasswordInput: "",
      secPasswordValid: false,

      submitDisabled: true,

      showToggle: false,
      showPassword: false,

      showSecToggle: false,
      showSecPassword: false,
    };
  },
  watch: {
    pageType() {
      this.emailInvalidMsg = "";
      this.passwordInvalidMsg = "";
    },
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
      if (this.secPasswordInput === this.passwordInput) {
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
      if (this.pageType === "Login") {
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
    checkEmail() {
      if (this.emailInput.length === 0) {
        // if email missing, show missing msg
        this.emailInvalidMsg = "please enter an email address";
      } else if (!this.validateEmail(this.emailInput)) {
        // if email invalid, show invalid msg
        this.emailInvalidMsg = "please use a valid email address";
      } else {
        this.emailInvalidMsg = "";
      }
    },
    checkPassword() {
      if (this.passwordInput.length === 0) {
        // if missing, show missing msg
        this.passwordInvalidMsg = "please enter a password";
      } else if (!this.validatePassword(this.passwordInput)) {
        // if invalid, show invalid msg
        this.passwordInvalidMsg =
          "Must contain at least 1 uppercase letter and a special character";
        this.passwordInvalid = true;
      } else {
        this.passwordInvalidMsg = "";
      }
    },
    checkSecPassword() {
      if (this.secPasswordInput.length === 0) {
        // if missing, show missing msg
        this.passwordInvalidMsg = "please enter a password";
        this.passwordInvalid = false;
      } else if (!this.validatePassword(this.secPasswordInput)) {
        // if invalid, show invalid msg
        this.passwordInvalidMsg =
          "Must contain at least 1 uppercase letter and a special character";
      } else if (
        this.pageType === "sign up" &&
        this.passwordInput !== this.secPasswordInput
      ) {
        // if passwords don't match, show no match msg
        this.passwordInvalidMsg = "Passwords don't match";
      } else {
        this.passwordInvalidMsg = "";
        this.passwordInvalid = false;
      }
    },
  },
};
</script>

<style scoped>
.forgot-pass {
  display: block;
  text-align: right;
  font-size: 0.75rem;
  margin-bottom: -16px;
}
a {
  color: #171717;
}
.email-signin {
  background-color: #fff;
  width: 100%;
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
  height: 50px;
  box-sizing: border-box;
  padding-left: 18px;
  border: 2px solid #95959560;
  border-radius: 4px;
  margin-top: 8px;
  transition: 0.2s ease-in;
}
.email-wrapper input {
  margin-bottom: 15px;
}
input::placeholder {
  color: #171717;
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
  margin-top: -32px;
  position: relative;
  left: 105px;
}
.toggle-sec-pass-container {
  margin-top: -32px;
  position: relative;
  left: 450px;
}
.toggle-pass-container img,
.toggle-sec-pass-container img {
  z-index: 10;
}

#pass-requirements {
  font-size: 0.75rem;
  margin-top: 0px;
  margin-bottom: 3px;
  margin-left: 0;
}
.invalid {
  color: #fa0521;
}

#invalid-email-msg,
#invalid-pass-msg {
  color: #fa0521;
  font-size: 0.75rem;
  text-align: left;
}

#invalid-email-msg {
  margin-top: -10px;
  margin-bottom: 20px;
}
#invalid-pass-msg {
  margin-top: 5px;
  width: 100%;
  margin-bottom: 10px;
}

button {
  width: 196px;
  height: 50px;
  background-color: #3843f1;
  color: #fff;
  border: none;
  outline: none;
  border-radius: 50px;
  display: block;
  margin: auto;
  margin-top: 20px;
  font-size: 0.875rem;
  font-weight: 600;
  transition: 0.1s ease-in;
}
button:hover {
  background-color: #28348a;
  cursor: pointer;
}
button:disabled {
  background-color: #d8d8d8;
}
button:disabled:hover {
  background-color: #d8d8d8;
  cursor: default;
}
</style>
