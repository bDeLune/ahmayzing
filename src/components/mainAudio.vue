<template>
  <div id="mainAudio">
    <button v-on:click="testAudio">TEST! </button>
    <div>Make sure your volume is turned down before pressing this</div>
  </div>
</template>
<script>


let audioCtx
if(window.AudioContext) {
  audioCtx = new AudioContext()
} else {
  audioCtx = new webkitAudioContext()
}

//create gain nodes for volume control
let gainNodeA = audioCtx.createGain();
let gainNodeB = audioCtx.createGain();
let gainNodeMaster = audioCtx.createGain();

export default {
  name: 'mainAudio',
  data () {
    return {
      msg: 'Main audio context'
    }
  },
      // Functions we will be using.
  methods: {
      testAudio: function(){
        //create sine wave node
        var sineA = audioCtx.createOscillator();
        sineA.frequency.value = 440;
        sineA.type = "sine";

        //create sine wave node
        var sineB = audioCtx.createOscillator();
        sineB.frequency.value = 220.00;
        sineB.type = "sine";
        
        var masterOut = audioCtx.destination;

        if (audioCtx){
          console.log('Audio context created successfully')
          //connect both sine waves to their respective gain nodes
          sineA.start();
          sineA.connect(gainNodeA);

          sineB.start();
          sineB.connect(gainNodeB); 

          //connect gain nodes to master gain node
          gainNodeA.connect(gainNodeMaster); 
          gainNodeB.connect(gainNodeMaster); 

          gainNodeMaster.connect(masterOut);
        }else{
          console.log('audio context doesnt exist')
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
