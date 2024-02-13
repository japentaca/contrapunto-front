
<template>
  <div id="output"></div>
  <button @click="dale">dale</button>
</template>


<script setup>
import { ref, onMounted } from 'vue'
import Vex from 'vexflow'
defineProps({
  msg: String,
})
let vf
let score = null
let system = null
const { Factory, EasyScore, System } = Vex.Flow;
onMounted(() => {

  vf = new Factory({
    renderer: { elementId: 'output', width: 800, height: 200 },
  });

  score = vf.EasyScore();
  system = vf.System();

})

async function dale() {
  system
    .addStave({
      voices: [
        score.voice(score.notes('C#5/q, B4, A4, G#4', { stem: 'up' })),
        score.voice(score.notes('C#4/h, C#4', { stem: 'down' })),
      ],
    })
    .addClef('treble')
    .addTimeSignature('4/4');

  vf.draw();

}



</script>


<style scoped>
.read-the-docs {
  color: #888;
}
</style>
