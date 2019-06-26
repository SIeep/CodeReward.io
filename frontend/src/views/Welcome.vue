<template>
  <div class="about">
    <!-- <h1>This is the login page</h1> -->
    <div class="list-accounts">
      <h2>This is test GET request to fetch and list all users from my DB:</h2>
      <div v-for="user in users">
        Username: {{user}}
      </div>
      {{teamTreehouseAccount}}
      <h2>This is test GET request to teamtreehouse for my profile:</h2>
      <div v-for="badge in teamTreehouseAccount.badges">
        Team Treehouse Account badge: {{badge.name}}
      </div>
      <h2>This is test GET request to codecademy for my profile:</h2>
      <div>
        {{codeCademyAccount}}
      </div>
    </div>
    <br>
    <div class="login">
      <form v-on:submit.prevent="submit()">
        <div class="row">
          <label for="my-username" class="sr-only">Username</label>
          <br>
          <input id="my-email" type="text" name="Username" title="Enter Username" placeholder="Your Username" v-model="username"/>
        </div>
        <div class="row">
          <label for="my-password" class="sr-only">Password</label>
          <br>
          <input id="my-password" type="text" name="password" title="Enter password" placeholder="Your password" v-model="password"/>
        </div>
      </form>
      <button>Login</button>
    </div>
  </div>
</template>

<script type="text/javascript">
  import axios from "axios";
  import Mercury from "@postlight/mercury-parser";

  const url="https://www.codecademy.com/lnsomniac";
  Mercury.parse(url).then(result => this.codeCademyAccount = response.data);

  export default {
    data: function() {
      return {
        users: "",
        teamTreehouseAccount: "",
        // codeCademyAccount: "",
      };
    },
    created: function() {
      axios.get("/api/users").then(response => {
        this.users = response.data;
      });
      axios.get("https://teamtreehouse.com/brandonevans5.json").then(response => {
        this.teamTreehouseAccount = response.data;
      });
      // axios.get("https://www.codecademy.com/users/lnsomniac").then(response => {
      //   this.codeCademyAccount = response.data;
      // });
    },
  }
</script>