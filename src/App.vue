<template>
 <Signup />
</template>

<script>
import Signup from './components/Signupform.vue'

export default {
  name: 'App',
  components: {Signup}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  text-align: center;
}
body{
  margin: 0;
  background: #eee;
}
</style>
