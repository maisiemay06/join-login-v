<template>
  <div class="social-signin">
    <h2>sign in</h2>
    <div class="social-button">
      <img src="../assets/li-logo.png" alt="Linkedin logo" />
      <p>Continue with Linkedin</p>
      <div class="spacer"></div>
    </div>
    <div class="social-button">
      <img src="../assets/g-logo.png" alt="Google logo" />
      <p>Continue with Google</p>
      <div class="spacer"></div>
    </div>
    <div class="social-button">
      <img src="../assets/fb-logo.png" alt="Facebook logo" />
      <p>Continue with Facebook</p>
      <div class="spacer"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SocialSignIn",
  props: {},
};
</script>

<style scoped>
.social-signin {
  width: 100%;
  margin: auto;
  margin-top: 148px;
  text-align: center;
}
.social-signin h2 {
  font-size: 1.875rem;
  font-weight: 600;
  margin-bottom: 44px;
}
.social-button {
  background-color: #fff;
  border: none;
  outline: none;
  border-radius: 9px;
  width: 100%;
  height: 48px;
  margin-bottom: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 25px;
  box-sizing: border-box;
  font-size: 1rem;
  font-weight: 500;
  transition: 0.1s ease-in;
}
img,
.spacer {
  width: 25px;
  height: 25px;
}

.social-button:hover {
  background-color: #eeeeee;
  cursor: pointer;
}
</style>
