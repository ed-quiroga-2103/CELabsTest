<template>
  <form @submit.prevent="login">
    <div class="grid-container">
        <input type="text" v-model="username" name="username" placeholder="Email">      
    </div>
    <div class="grid-container">
        <input class="text" type="password" v-model="password" name="password" placeholder="Password">
    </div>
    <div class="grid-container">
        <input type="submit" value="Log In" class="btn">
    </div>
  </form>
</template>

<script>
import axios from 'axios';

export default {
  name: 'LogIn',
  data(){
    return{
      username: '',
      password: '',
      posts: [],
      errors: []
    }
  },
  methods: {
    login(){
      axios.post(`http://127.0.0.1:5001/login`, {}, {
        auth: {
          username: this.username,
          password: this.password
        }
      }).then(response => {
        this.posts = response.data;
        console.log(this.posts['token']);
      }
      );
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
.grid-container {
  display: grid;
  grid-template-columns: auto auto;
}
</style>
