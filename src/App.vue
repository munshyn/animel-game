<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
    <img alt="Vue logo" class="block m-auto" src="@/assets/animel-icon-big.png" width="125" height="125" />
    <div class="music-player">
      <audio
        ref="audio"
        src="@/assets/bg-music.mp3"
        autoplay
        loop
        id="audio"
      ></audio>
      <audio>
        <source src="@/assets/bg-music.mp3" type="audio/mpeg">
      </audio>
    <div @click="toggleSound()" class="toggle-sound"></div>
  </div>
    <div class="flex justify-center">
      <div class="bg-white text-black w-1/3 flex justify-between">
        <div class="self-center text-2xl nes-text">
          rabbit
        </div>
        <div class="flex flex-col">
          <div class="choices">
            carrot
          </div>
          <div>
            apple
          </div>
          <div>
            grain
          </div>
  
        </div>

      </div>

    </div>
</template>

<style scoped>
.choices {
  padding: 0.2rem;
}
</style>
