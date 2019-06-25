<template>
  <div class="about">
    <h1>This is the login page</h1>
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
