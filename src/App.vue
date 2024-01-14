<script setup>
import { ref } from 'vue';
import bgMusic from './assets/bg-music.mp3'
import Level1 from './components/Level1.vue';
import Level2 from './components/Level2.vue';
import Level3 from './components/Level3.vue';

const level = ref(1)

const audioPlay = ref(false)
const audio = new Audio(bgMusic)

const toggleAudio = () => {
  audioPlay.value = true
  audio.play()
  audio.loop = true
}

const nextLevel = (data) => {
  if(data === true) {
    level.value++
  } else {
    level.value--
  }
}
</script>

<template>
  <div v-if="audioPlay === false"
    class="m-auto flex justify-center items-center"
    style="
      width: 100vw;
      height : 100vh;
      background-color: #222222;
      color: azure;"
  >
    <div>
      <p class="text-5xl">Welcome to Animel Game</p>
      <i class="block my-5 mx-auto nes-octocat animate nes-pointer" @click="toggleAudio"></i>
      <p class="text-center typewriter">Click the cat to continue...</p>
    </div>    
  </div>
  <div v-else>
    <div class="flex flex-nowrap">
      <div class="flex justify-center items-center"
        style="
          writing-mode: vertical-lr;
          width: 16.67%;
          height : 100vh;
          background-color: #222222;
          color: azure;
          text-orientation: upright;"
      >
        <p class="text-4xl tracking-widest">Animel Game</p>
      </div>
      <div class="w-2/3 flex flex-col items-center">
        <i class="block my-5 mx-auto nes-octocat animate"></i>
        <Level1 v-if="level === 1"></Level1>
        <Level2 v-if="level === 2"></Level2>
        <Level3 v-if="level === 3"></Level3>
        <div :class="['flex w-5/6 mt-3', {
          'justify-between' : level === 2,
          'justify-end' : level === 1
        }]">
          <button v-if="level !== 1" class="nes-btn is-warning" @click="nextLevel(false)">Previous Level</button>
          <button v-if="level !== 3"  class="nes-btn is-primary" @click="nextLevel(true)">Next Level</button>
        </div>      
      </div>
      <div class="flex justify-center items-center"
        style="
          writing-mode: vertical-lr;
          width: 16.67%;
          height : 100vh;
          background-color: #222222;
          color: azure;
          text-orientation: upright;"
      >
        <p class="text-4xl tracking-widest">Animel Game</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.choices {
  padding: 0.2rem;
}
</style>
