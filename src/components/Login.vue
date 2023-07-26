<template>
  <center>
    <div class="hello">
      <center><h1>Login Form</h1></center>

      <div>
        <input
          class="name"
          type="text"
          placeholder="Enter Your Email"
          name=""
          v-model="login.email"
          required
        /><br /><br />
        <input
          class="name"
          type="password"
          placeholder="Enter Password Please"
          name=""
          required
          v-model="login.password"
        /><br /><br />

        <center>
          <router-link to="/todo">
            <button class="btn" v-on:click="loginUser()">Login</button>
          </router-link>
          <!-- <router-link to="/todo">
            <button class="btn">Todo</button>
          </router-link> -->
        </center>
      </div>
      <p>
        Email is :> {{ this.login.email }}<br />
        Password is :> {{ this.login.password }}
      </p>
    </div>
  </center>
</template>

<script>
export default {
  name: "Login",

  data() {
    return {
      login: {
        password: null,
        email: null,
      },
    };
  },
  methods: {
    loginUser() {
      if (!this.validEmail()) return;
      if (!this.validPassword()) return;
    },
    validEmail() {
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      if (!emailRegex.test(this.login.email)) {
        alert("Invalid");
        return false;
      }
      return true;
    },
    validPassword() {
      if (!/^[A-Z]/.test(this.login.password)) {
        alert("Must start with Capital letter");
        return false;
      }
      if (this.login.password.length < 8) {
        alert("length Must contain 8 character ");
        return false;
      }
      return true;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.name {
  width: 400px;
  height: 30px;
  border-radius: 18px;
  margin: 10px;
  padding: 5x;
  background: rgb(204, 230, 231);
  color: black;
  font-family: "Courier New", Courier, monospace;
  font-size: larger;
  margin-top: 20px;
}

.btn {
  width: 150px;
  height: 30px;
  border-radius: 19px;
  color: chocolate;
  font-size: 14px;
  margin: 10px;
  padding: 5px;
  margin-top: 50px;
  background: rgb(204, 230, 231);
  cursor: pointer;
  border: 1px solid;
}

.hello {
  height: 500px;
  width: 500px;
  border-radius: 40px;
  margin-top: 30px;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  font-weight: 400px;
  margin: 0;
  padding: 0;
  background-color: lightslategrey;
  border: 3px solid;
}
</style>
