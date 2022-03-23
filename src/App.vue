<template>
 <Signup/>
</template>

<script>
import Signup from './components/SignupForm.vue'
export default {
  
  name: 'App',
  components: {Signup}
}
</script>

<style>
#app {

  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

 *{
        font-family: 'Roboto Mono', monospace;
    }
    
body{
  margin: 0;
  background: rgb(50, 49, 49);
}
</style>
