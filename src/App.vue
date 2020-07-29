<template>
  <div id="app">
    <!-- LogIn /-->
    <Worklog/>
    <!--Reservation /-->
    <!--Palmadas /-->
  </div>
</template>


<script>
import LogIn from './components/LogIn';
import Register from './components/Register';
import Reservation from './components/Reservation';
import Palmadas from './components/Palmadas'
import Worklog from './components/Worklog'

export default {
  name: 'App',
  components: {
    //LogIn
    Worklog
    //Reservation
    //Palmadas
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
