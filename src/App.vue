<template>
  <SignupComponent />
</template>

<script>
import SignupComponent from './components/SignupComponent.vue'

export default {
  name: 'App',
  components: {
    SignupComponent
  }
}
</script>

<style>
  @font-face {
    font-family: 'Fira Code', monospace;
    src: url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@300&display=swap');
  }
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #d8dee9;
  }
  body {
    background-color: #d8dee9;
  }
</style>
