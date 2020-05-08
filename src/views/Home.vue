<template>
  <div class="home">
    <div class="form-container" v-show="showForm">
      <h1>Join the Web Developers Club!</h1>
      <p>Sign up to access our special, secret page. Just create an account and answer a brief survey.</p>
      <p class="error" v-show="showError">Please check that all fields are populated.</p>

      <form v-on:submit.prevent="validateForm">
        <fieldset>
          <legend>Create an Account</legend>
          <p>
            <label>
              Username
              <input type="text" name="username" tabindex="0" v-model="username" />
            </label>
          </p>
          <p>
            <label>
              Email
              <input type="text" name="email" tabindex="0" v-model="email" />
            </label>
          </p>
          <p>
            <label>
              Password
              <input type="text" name="password" tabindex="0" v-model="password" />
            </label>
          </p>
          <p>
            <label>
              Verify Password
              <input
                type="text"
                name="passwordVerify"
                tabindex="0"
                v-model="passwordVerify"
              />
            </label>
          </p>
        </fieldset>
        <p>
          <input type="submit" value="Submit" />
        </p>
      </form>
    </div>

    <div class="success-message" v-show="!showForm">
      <h1>Thank you for signing up!</h1>
      <p>
        Please take our new member survey.
        <router-link to="/survey">Click here</router-link>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      username: "",
      email: "",
      password: "",
      passwordVerify: "",
      showForm: true,
      showError: false
    };
  },
  methods: {
    validateForm: function() {
      if (
        this.username != "" &&
        this.email != "" &&
        this.password === this.passwordVerify
      ) {
        this.showForm = false;
      } else {
        this.showError = true;
      }
    }
  }
};
</script>

//!-- TODO "scoped" attribute to limit CSS to this component only -->

<style scoped>
.error {
  border: 1px solid #aa0000;
  padding: 1rem;
  color: #aa0000;
}
h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>