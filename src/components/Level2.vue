<script setup>
import { ref } from 'vue';

const isCorrect = ref()
const chosenAnswer = ref('')

const checkAnswer = (answer,choice) => {
  chosenAnswer.value = choice
  if(answer) {
    isCorrect.value = true
  }
  else {
    isCorrect.value = false
  }
}
</script>


<template>
    <div class="w-full nes-container with-title">
        <p class="title">Level 2</p>
        <div class="flex flex-col">
          <div class="flex">
            <img class="w-28" src="@/assets/8-bit-moon.png" alt="rabbit">
            <div class="nes-balloon from-left">
              <p class="typewriter">How far is the moon from earth?</p>
            </div>
          </div>
          <div class="flex flex-row-reverse">
            <i class="ml-3 self-end nes-bcrikko"></i>
            <div class="nes-balloon from-right capitalize is-dark">
              <p v-if="isCorrect === true" class="is-success">{{ chosenAnswer }}</p>
              <p v-else-if="isCorrect === false" class="is-danger">{{ chosenAnswer }}</p>
              <div v-else class="flex flex-col gap-1">
                <button class="nes-btn" @click="checkAnswer(false,'843k km')">843k km</button>
                <button class="nes-btn" @click="checkAnswer(false,'483k km')">483k km</button>
                <button class="nes-btn" @click="checkAnswer(true,'384k km')">384k km</button>
              </div>
            </div>
          </div>
          <div v-if="isCorrect === true" class="flex">
            <img class="w-28" src="@/assets/8-bit-moon.png" alt="rabbit">
            <div class="nes-balloon from-left">
              <p class="typewriter">Why aren't you a scientist yet? <i class="nes-icon star"></i></p>
              
            </div>
          </div>
          <div v-else-if="isCorrect === false && isCorrect !== null" class="flex">
            <img class="w-28" src="@/assets/8-bit-moon.png" alt="rabbit">
            <div class="nes-balloon from-left">
              <p class="typewriter">Nope, too far <i class="nes-icon close"></i></p>
            </div>
          </div>
        </div>
      </div>
</template>