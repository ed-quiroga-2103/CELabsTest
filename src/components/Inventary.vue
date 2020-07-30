<template>
  <form @submit.prevent="inventary">
    <div class="grid-container">
        <input type="text" v-model="date" name="date" placeholder="Date">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="complete_computers" name="complete_computers" placeholder="Number of complete computers">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="incomplete_computers" name="incomplete_computers" placeholder="Number of incomplete computers">      
    </div>
    
    <div class="grid-container">
        <input type="text" v-model="number_projectors" name="number_projectors" placeholder="Number of projectors">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="number_chairs" name="number_chairs" placeholder="Number of chairs">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="number_fire_extinguishers" name="number_fire_extinguishers" placeholder="Number of Fire Extinguishers">      
    </div>

    <div class="grid-container">
        <input type="text" v-model="lab" name="lab" placeholder="Laboratory">      
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
  name: 'Inventary',
  data(){
    return{
      date: '',
      complete_computers: '',
      incomplete_computers: '',
      number_projectors: '',
      number_chairs: '',
      number_fire_extinguishers: '',
      lab: '',
      token: '',
      posts: [],
      errors: [],
    }
  },

  methods: {
    inventary()
    {
        var data = JSON.stringify(

          {"date":this.date,
          "complete_computers": this.complete_computers,
          "incomplete_computers": this.incomplete_computers,
          "number_projectors": this.number_projectors,
          "number_chairs": this.number_chairs,
          "number_fire_extinguishers": this.number_fire_extinguishers,
          "lab": this.lab
          }
        
          );
        var config = {
        method: 'post',
        url: 'http://127.0.0.1:5001/inventary',
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
