<template>
  <nav>
    <a href="https://meeow.com/">
      <img src="./assets/logo.png" alt="Meeow logo" id="logo" />
    </a>
  </nav>
  <div class="container">
    <SocialSignIn />
    <div class="section-title">
      <span class="line"></span>
      <h2>OR</h2>
      <span class="line"></span>
    </div>
    <EmailSignIn :pageType="pageType" />
    <p v-if="pageType === 'signin'" class="footer">
      Not a member yet?
      <a href="" @click.prevent="pageType = 'join'">Click here to join</a>
    </p>
    <p v-else class="footer">
      Already a member?
      <a href="" @click.prevent="pageType = 'signin'">Click here to signin</a>
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
      pageType: "signin",
    };
  },
};
</script>

<style>
body {
  background-color: #f2f3f6;
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
  height: 95px;
  background-color: #fff;
  position: fixed;
  top: 0;
  left: 0;
  box-sizing: border-box;
  padding: 40px 0;
}
#logo {
  width: 140px;
  height: 25px;
}
.container {
  margin: auto;
  width: 90%;
  max-width: 590px;
}
.section-title {
  width: 100%;
  margin: auto;
  margin-top: 50px;
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
  margin: 0 17px;
}
.footer,
.footer a {
  font-size: 0.875rem;
  color: #171717;
  margin-top: 25px;
  padding-bottom: 50px;
}
</style>
