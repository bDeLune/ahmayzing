<template>
  <div id="app">
    <img id="logo" src="./assets/ahh3.png">
    <router-view/>
  </div>
</template>

<script>
import navigation from './components/testAudio.vue'

export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #884200;
}

body{
  background: black;
}

#logo{
  padding: 20% 0 0 120px;
}



h1{
  color: rgba(22, 1, 141, 0.548);
}
</style>
