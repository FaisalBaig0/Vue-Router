<template>
  <center>

  
  <div class="hello">
    <center><h1>Sign Up</h1></center>

    <div>
      <center><label for="fullName">Full Name:</label></center>

      <input
        class="name"
        type="text"
        placeholder="Enter Your Name"
        name="name"
        v-model="signup.name"
        required
      />
      <div />
      <br /><br />
      <div>
        <center><label for="email">Email:</label></center>
        <input
          class="name"
          type="text"
          placeholder="Enter Your Email"
          name="email"
          v-model="signup.email"
          required
        />
      </div>
      <br /><br />

      <div>
        <center><label for="password">Password:</label></center>

        <input
          class="name"
          type="password"
          placeholder="Enter Password Please"
          name="password"
          v-model="signup.password"
          required
        />
      </div>
      <br /><br />
      <div>
        <center>
          <label for="confirmPassword">Confirm Password:</label>
        </center>

        <input
          class="name"
          type="password"
          placeholder="Confirm Password"
          name="cpassword"
          v-model="signup.cpassword"
          required
        />
      </div>
      <br /><br />
      <div>
        <button class="btn" v-on:click="signupUser()">Sign Up</button>
        <router-link to="/login">
           <button class="btn" v-on:click="goToLogin">Login</button>
        </router-link>
        
      </div>
    </div>
   <center><p>
      Name: >  {{ this.signup.name }}<br />
      Email: > {{ this.signup.email }}<br />
      Password: > {{ this.signup.password }}
    </p>
    </center> 
  </div>
  </center>
</template>

<script>
export default {
  name: "Signup",
  data() {
    return {
      signup: {
        name: null,
        password: null,
        email: null,
        cpassword: null,
      },
    };
  },
  methods: {
    signupUser() {
      if (!this.validateUsername()) return;
      if (!this.validatePassword()) return;
      if (!this.validateEmail()) return;
      if (this.signup.password !== this.signup.cpassword) {
        alert("Passwords do not match!");
        return;
      }

      // Form submission logic here
      // console.log("Form submitted successfully!");
      // console.log("Name:", this.signup.name);
      // console.log("Email:", this.signup.email);
      // console.log("Password:", this.signup.password);
    },
    validateUsername() {
      if (/\s/.test(this.signup.name)) {
        alert("Username cannot contain spaces.");
        return false;
      }

      if (!/[0-9!@#$%^&*(),.?":{}|<>]/.test(this.signup.name)) {
        alert("Username must include a number or special character.");
        return false;
      }

      return true;
    },
    validatePassword() {
      if (!/[!@#$%^&*(),.?":{}|<>]/.test(this.signup.password)) {
        alert("Password must include a special character.");
        return false;
      }

      if (!/^[A-Z]/.test(this.signup.password)) {
        alert("Password must start with a capital letter.");
        return false;
      }

      if (this.signup.password.length < 8) {
        alert("Password must be at least 8 characters long.");
        return false;
      }

      return true;
    },
    validateEmail() {
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      if (!emailRegex.test(this.signup.email)) {
        alert("Invalid email format.");
        return false;
      }

      return true;
    },
    goToLogin() {
      this.$router.push('/login'); // Redirect to the login page
    },
  },
  computed: {},
};
</script>

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
}

.btn {
  width: 150px;
  height: 30px;
  background-color: #42b983;
  border-radius: 19px;
  color: chocolate;
  font-size: 14px;
  margin: 10px;
  padding: 1px;
  margin-top: 50px;
  cursor: pointer;
}

.hello {
  background-color: #42b983;
  height: 600px;
  width: 500px;
  border-radius: 40px;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  font-weight: 400px;
}
h1 {
  align-items: center;
  justify-content: center;
}
</style>
