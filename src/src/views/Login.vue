<template>
  <div id="fromLogin">
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <div class="container">
      <div class="row">
        <div class="col-sm-4">
          <img style="width: 100%" src="../assets/vineyardgif.gif" />
        </div>
        <div class="container col-sm-6">
          <h1>Login</h1>
          <form v-on:submit.prevent="login()">
            <div class="form-group">
              <label for="exampleInputEmail1">Email:</label>
              <input
                type="email"
                class="form-control"
                id="exampleInputEmail1"
                aria-describedby="emailHelp"
                placeholder="Enter email"
                required
                v-model="emailLogin"
              />
              <small id="emailHelp" class="form-text text-muted"
                >We'll never share your email with anyone else.</small
              >
            </div>
            <div class="form-group">
              <label for="passwordLogin">Password:</label>
              <input
                type="password"
                class="form-control"
                id="passwordLogin"
                placeholder="Password"
                v-model="passwordLogin"
              />
            </div>
             <button type="submit" class="button btn-primary float-right">
              Iniciar Sessão
            </button>
            <button id="registerBtn" type="button" class="button btn-link float-right">
              <router-link style="color: black; text-decoration: none;" to="/register">Registar</router-link>
            </button>
           
          </form>
        </div>
      </div>
    </div>
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />

  
  </div>
</template>

<script>
export default {
  data: () => ({
    emailLogin: "",
    passwordLogin: ""
  }),
  created: function() {
    window.addEventListener("unload", this.saveStorage);
    if (localStorage.getItem("loggedUser")) {
      this.$store.state.loggedUser = JSON.parse(
        localStorage.getItem("loggedUser")
      );
    }
    if (localStorage.getItem("users")) {
      this.$store.state.users = JSON.parse(localStorage.getItem("users"));
    }
  },
  methods: {
    login() {
      this.$store.commit("LOGIN", {
        emailLogin: this.emailLogin,
        passwordLogin: this.passwordLogin
      });
    }
  },
  saveStorage() {
    localStorage.setItem("users", JSON.stringify(this.$store.state.users));
  }
};



</script>

<style>
.button {
  background-color: #555555; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  font-family: "Cinzel", serif;
}

.button:hover {
  background-color: black;
}


#registerBtn{
  font-family: "Cinzel", serif;
   background-color: white;
   border: none;
 
}
h1 {
  font-family: "Cinzel", serif;
}


label{
  font-family: "Didact Gothic", sans-serif;
}


@import url("https://fonts.googleapis.com/css?family=Cinzel&display=swap");

@import url("https://fonts.googleapis.com/css?family=Didact+Gothic&display=swap");
</style>
