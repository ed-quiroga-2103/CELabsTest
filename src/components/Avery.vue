<template>
  <form @submit.prevent="avery">
    <div class="grid-container">
        <input type="text" v-model="date_time" name="date_time" placeholder="Date and Time">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="id_fault_part" name="id_fault_part" placeholder="Id of the Fault Part">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="description" name="description" placeholder="Description of the Fault Part">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="token" name="token" placeholder="Token">      
    </div>

    <div class="grid-container">
        <input type="submit" value="Send Avery Report" class="btn">
    </div>
  </form>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Avery',
  data(){
    return{
      date_time: '',
      id_fault_part: '',
      description: '',
      token: '',
      posts: [],
      errors: [],
    }
  },

  methods: {
    avery()
    {
        var data = JSON.stringify(

          {"date_time":this.date_time,
          "id_fault_part": this.id_fault_part,
          "description": this.description,
          }
        
          );
        var config = {
        method: 'post',
        url: 'http://127.0.0.1:5001/avery',
        headers: { 
            'x-access-token': this.token, 
            'Authorization': 'Basic QWRtaW46MTIzNDU=', 
            'Content-Type': 'application/json'
        },
            data: data
        };

        axios(config) 
        .then(response => {
        this.posts = response.data;
        console.log(this.posts['message']);
      }
      ).catch(error =>{
        console.log(error.data['message'])
      });
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
