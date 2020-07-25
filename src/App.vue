<template>
  <div id="app">
    <LogIn />
  </div>
</template>


<script>
import LogIn from './components/LogIn';

export default {
  name: 'App',
  components: {
    LogIn
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
