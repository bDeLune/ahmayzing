<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
        <mainAudio></mainAudio>
  </div>
</template>

<script>
import mainAudio from './mainAudio.vue';

export default {
  name: 'HelloWorld',
  components:{mainAudio},
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
