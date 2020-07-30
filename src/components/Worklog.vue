<template>
  <form @submit.prevent="worklog">
    <div class="grid-container">
        <input type="text" v-model="date_time" name="date_time" placeholder="Date/Time">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="init_time" name="init_time" placeholder="Initialization Time">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="final_time" name="final_time" placeholder="Finalization Time">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="description" name="description" placeholder="Description">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="token" name="token" placeholder="Token">      
    </div>

    <div class="grid-container">
        <input type="submit" value="Send Hours Report" class="btn">
    </div>
  </form>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Worklog',
  data(){
    return{
      date_time: '',
      init_time: '',
      final_time: '',
      description: '',
      token: '',
      posts: [],
      errors: [],
    }
  },

  methods: {
    worklog()
    {
        var data = JSON.stringify(

          {"date_time":this.date_time,
          "init_time": this.init_time,
          "final_time": this.final_time,
          "description": this.description,
          }
        
          );
        var config = {
        method: 'post',
        url: 'http://127.0.0.1:5001/worklog',
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
