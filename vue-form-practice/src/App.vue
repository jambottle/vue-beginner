<template>
  <form v-on:submit.prevent="submitForm">
    <div>
      <label for="username">ID: </label>
      <input id="username" type="text" v-model="username" />
    </div>
    <div>
      <label for="password">PW: </label>
      <input id="password" type="password" v-model="password" />
    </div>
    <button type="submit">Sign in</button>
  </form>
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',

  data() {
    return {
      username: '',
      password: '',
    };
  },

  methods: {
    submitForm: function () {
      // event.preventDefault();
      console.log(this.username, this.password);

      const url = 'https://jsonplaceholder.typicode.com/users';
      const data = {
        username: this.username,
        password: this.password,
      };
      axios
        .post(url, data)
        .then(function (response) {
          console.log(response);
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
};
</script>

<style lang="scss" scoped></style>
