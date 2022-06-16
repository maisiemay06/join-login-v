<template>
  <nav>
    <a href="https://meeow.com/">
      <img src="./assets/logo-blue.png" alt="Meeow logo" id="logo" />
    </a>
  </nav>
  <div class="container">
    <h2 class="page-title">{{ pageType }}</h2>

    <div class="social-account-already">
      <div class="spacer"></div>
      <p>
        Please log in with the socail account you registered with. <br />
        Or you may reset your password here.
      </p>
      <a href="">&times;</a>
    </div>

    <p v-if="pageType === 'Login'" class="switch-page">
      Not a member yet?
      <a href="" @click.prevent="pageType = 'sign up'">Click here to join</a>
    </p>
    <p v-else class="switch-page">
      Already a member?
      <a href="" @click.prevent="pageType = 'Login'">Click here to signin</a>
    </p>
    <SocialSignIn />
    <div class="section-title">
      <span class="line"></span>
      <h2>OR</h2>
      <span class="line"></span>
    </div>
    <EmailSignIn :pageType="pageType" />
    <p class="footer">
      Experiencing issues? Click on the speech bubble in the bottom right hand
      corner
    </p>
  </div>
</template>

<script>
import SocialSignIn from "./components/SocialSignIn.vue";
import EmailSignIn from "./components/EmailSignIn.vue";

export default {
  name: "App",
  components: {
    SocialSignIn,
    EmailSignIn,
  },
  data() {
    return {
      pageType: "Login",
    };
  },
};
</script>

<style>
body {
  background-color: #f4f4f4;
  font-family: sofia-pro, sans-serif;
  font-weight: 400;
  font-style: normal;
  font-size: 16px;
  color: #171717;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
nav {
  width: 100%;
  margin: 60px 0 0 55px;
  text-align: left;
}
#logo {
  width: 168px;
  height: 30px;
}
.container {
  margin: auto;
  width: 90%;
  max-width: 550px;
  margin-top: -80px;
  text-align: center;
}
.page-title {
  font-size: 3.75rem;
  font-weight: 400;
  margin-bottom: 24px;
  z-index: 1;
}

.social-account-already {
  background-color: #fc4949;
  color: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  border-radius: 6px;
  box-shadow: 0px 1px 3px 0px #000;
  font-size: 0.938rem;
  margin-top: -90px;
  z-index: 10;
  display: none;
}
.social-account-already .spacer {
  width: 20px;
}
.social-account-already a {
  width: 20px;
  color: #fff;
  text-decoration: none;
  font-weight: 100;
  font-size: 3rem;
  margin-top: -8px;
}

.switch-page,
.switch-page a {
  font-size: 0.875rem;
  color: #171717;
  margin-bottom: 36px;
}
.section-title {
  width: 100%;
  margin: 32px auto;
  display: flex;
  flex: 1;
  line-height: 1rem;
  align-items: center;
}
.section-title .line {
  border: 1px solid #bbbbbb;
  width: 100%;
  height: 0;
  opacity: 50%;
}
.section-title h2 {
  font-weight: 600;
  font-size: 1.563rem;
  color: #c3c3c3;
  margin: 0 2px;
}
.footer {
  font-size: 0.75rem;
  margin-top: 36px;
  padding-bottom: 60px;
}

@media only screen and (max-width: 480px) {
  nav {
    text-align: center;
    margin-left: 0;
  }
  .container {
    margin-top: -30px;
  }
}
</style>
