<template>
  <form @submit.prevent="reservation">
    <div class="grid-container">
        <input type="text" v-model="request_date" name="request_date" placeholder="Request Date">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="requested_date" name="requested_date" placeholder="Requested Date">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="init_time" name="init_time" placeholder="Initialization Time">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="final_time" name="final_time" placeholder="Finalization Time">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="subject" name="subject" placeholder="Subject">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="description" name="description" placeholder="Description">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="operator" name="operator" placeholder="Operator">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="token" name="token" placeholder="Token">      
    </div>

    <div class="grid-container">
        <input type="submit" value="Made Reservation" class="btn">
    </div>
  </form>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Reservation',
  data(){
    return{
      request_date: '',
      requested_date: '',
      init_time: '',
      final_time: '',
      subject: '',
      description: '',
      operator: '',
      token: '',
      posts: [],
      errors: [],
    }
  },

  methods: {
    reservation()
    {
        var data = JSON.stringify(

          {"request_date":this.request_date,
          "requested_date":this.requested_date,
          "init_time": this.init_time,
          "final_time": this.final_time,
          "subject": this.subject,
          "description": this.description,
          "operator": this.operator
          }

          );
        var config = {
        method: 'post',
        url: 'http://127.0.0.1:5001/reservation',
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
