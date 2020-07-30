<template>
  <div id="app">
    <ShowReservations />
    <!-- Register / -->
    <!-- <Reservation /> -->
  </div>
</template>


<script>
import LogIn from './components/LogIn';
import Register from './components/Register';
import Reservation from './components/Reservation';
import ShowReservations from './components/ShowReservations';
import AllNighters from './components/AllNighters'

export default {
  name: 'App',
  components: {
    //LogIn
    //Register
    ShowReservations
  }
}
</script>

<!-- Style from App.vue is global -->
<style>
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body{
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
  background: rgb(248, 240, 233);
}


</style>
