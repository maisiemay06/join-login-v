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
        />
      </span>
      <span class="password-wrapper">
        <label for="password">Password</label>
        <input
          type="password"
          name="password"
          id="password"
          placeholder="Password"
        />
        <input
          v-if="pageType === 'join'"
          type="sec-password"
          name="sec-password"
          id="sec-password"
          placeholder="Re-enter password"
        />
      </span>
      <a href="">Forgotten password?</a>
      <button disabled>sign-in</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "EmailSignIn",
  props: {
    pageType: String,
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
}
.email-wrapper input {
  margin-bottom: 15px;
}
a {
  color: #171717;
  font-size: 0.75rem;
  text-align: center;
  display: block;
  margin-top: 36px;
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
