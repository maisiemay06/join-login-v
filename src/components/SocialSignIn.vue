<template>
  <div class="social-signin">
    <div class="social-button">
      <img src="../assets/fb-logo.png" alt="Facebook logo" />
      <p>Continue with Facebook</p>
      <div class="spacer"></div>
    </div>
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
  </div>
</template>

<script>
export default {
  name: "SocialSignIn",
  props: {},
};
</script>

<style scoped>
.social-button {
  background-color: #fff;
  border: 3px solid transparent;
  outline: none;
  border-radius: 9px;
  width: 100%;
  height: 67px;
  margin-bottom: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  box-sizing: border-box;
  font-size: 1rem;
  font-weight: 500;
  transition: 0.3s ease-in-out;
}
img,
.spacer {
  width: 28px;
  height: 28px;
}

.social-button:hover {
  cursor: pointer;
  border: 3px solid black;
}
</style>
