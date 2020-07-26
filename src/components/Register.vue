<template>
  <form @submit.prevent="register">
    <div class="grid-container">
        <input type="text" v-model="name" name="name" placeholder="Name">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="lastname1" name="lastname1" placeholder="Last Name">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="lastname2" name="lastname2" placeholder="Second Last Name">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="id_number" name="id_number" placeholder="ID Number">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="email" name="email" placeholder="Email">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="phone_number" name="phone_number" placeholder="Phone Number">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="university_id" name="university_id" placeholder="University ID">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="password" name="password" placeholder="Password">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="user_type" name="user_type" placeholder="User Type">      
    </div>

    <div class="grid-container">
        <input type="submit" value="Sign Up" class="btn">
    </div>
  </form>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Register',
  data(){
    return{
      name: '',
      lastname1: '',
      lastname2: '',
      id_number: '',
      email: '',
      phone_number: '',
      studentid: '',
      password: '',
      university_id: '',
      user_type: '',
      posts: [],
      errors: [],
    }
  },

  methods: {
    register(){
        axios.post(`http://127.0.0.1:5001/user`, 
           {
                name: this.name,
                lastname1: this.lastname1,
                lastname2: this.lastname2,
                id_number: this.id_number,
                password: this.password,
                email: this.email,
                phone_number: this.phone_number,
                university_id: this.university_id,
                user_type: this.user_type
            }
        ) 
        .then(response => {
        this.posts = response.data;
        console.log(this.posts['message']);
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
