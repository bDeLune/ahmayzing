<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>


//Begin Web Audio API context
let audioContext
if(window.AudioContext) {
  audioContext = new AudioContext()
} else {
  audioContext = new webkitAudioContext()
}

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'all your bass are belong to us'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
</style>
