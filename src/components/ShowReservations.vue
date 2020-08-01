<template>
    <div>
        <h3>Reservations</h3>
        <form @submit.prevent="login">
            <div class="grid-container">
                <input class="text" type="text" v-model="path" name="path" placeholder="Path">
            </div>
            <div class="grid-container">
                <input class="text" type="text" v-model="token" name="Token" placeholder="Token">
            </div>
        </form>
        <button v-on:click="getInfo()"> GET </button>
        <div>
            <ReservationInfo v-bind:info="info"/>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import ReservationInfo from './ReservationInfo'

export default {
  name: 'ShowReservations',
  data(){
    return{
      token: '',
      path: '',
      posts: [],
      errors: [],
      info: ''
    }
  },
  components:{
      ReservationInfo
  },
  methods: {
    getInfo(){       
        var data = '';
        var config = {
        method: 'get',
        url: 'http://127.0.0.1:5001/' + this.path,
        headers: { 
            'x-access-token': this.token, 
            'Authorization': 'Basic QWRtaW46MTIzNDU=', 
            'Content-Type': 'application/json'
        },
            data: data
        };

        axios(config).then(response=>{
            this.info = JSON.stringify(response.data)
        })
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
