<template>
  <div id="testAudio">
    <button v-on:click="createTestAudio">TEST! </button>
      <div>Make sure your volume is turned down before pressing this</div>
  </div>
</template>

<script>
export default {
  name: 'testAudio',
  data () {
    return {
      msg: 'Test Audio',
      contextCreated: false,
    }
  },
      // Functions we will be using.
  methods: {
      createTestAudio: function(){
        
        //Create audio context - should probably do this in our main component
        var audioCtx = new AudioContext()
        this.contextCreated = true;
  
        //create sine wave node
        var sineA = audioCtx.createOscillator();
        sineA.frequency.value = 440;
        sineA.type = "sine";

        //create sine wave node
        var sineB = audioCtx.createOscillator();
        sineB.frequency.value = 523.25;
        sineB.type = "sine";

        //create gain node for volume control, not implemented yet
        var gainNodeA = audioCtx.createGain();
        var masterOut = audioCtx.destination;

        if (audioCtx){
          console.log('Audio context created successfully')
          //connect both sine waves to master out node and play
          sineA.start();
          sineA.connect(masterOut);

          sineB.start();
          sineB.connect(masterOut); 
        }else{
          console.log('problem creating audio context')
        }
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

button {
  background: #3498db;
  background-image: -webkit-linear-gradient(top, #3498db, #2980b9);
  background-image: -moz-linear-gradient(top, #3498db, #2980b9);
  background-image: -ms-linear-gradient(top, #3498db, #2980b9);
  background-image: -o-linear-gradient(top, #3498db, #2980b9);
  background-image: linear-gradient(to bottom, #3498db, #2980b9);
  -webkit-border-radius: 28;
  -moz-border-radius: 28;
  border-radius: 28px;
  font-family: Arial;
  color: #ffffff;
  font-size: 20px;
  padding: 10px 20px 10px 20px;
  text-decoration: none;
}

button:hover {
  background: #3cb0fd;
  background-image: -webkit-linear-gradient(top, #3cb0fd, #3498db);
  background-image: -moz-linear-gradient(top, #3cb0fd, #3498db);
  background-image: -ms-linear-gradient(top, #3cb0fd, #3498db);
  background-image: -o-linear-gradient(top, #3cb0fd, #3498db);
  background-image: linear-gradient(to bottom, #3cb0fd, #3498db);
  text-decoration: none;
}


</style>
