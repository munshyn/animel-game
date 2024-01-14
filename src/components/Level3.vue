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
        <p class="title">Level 3</p>
        <div class="flex flex-col">
          <div class="flex">
            <img class="w-28" src="@/assets/8-bit-lungs.png" alt="rabbit">
            <div class="nes-balloon from-left">
              <p class="typewriter">How many times does human breath in a day?</p>
            </div>
          </div>
          <div class="flex flex-row-reverse">
            <i class="ml-3 self-end nes-bcrikko"></i>
            <div class="nes-balloon from-right capitalize is-dark">
              <p v-if="isCorrect === true" class="is-success">{{ chosenAnswer }}</p>
              <p v-else-if="isCorrect === false" class="is-danger">{{ chosenAnswer }}</p>
              <div v-else class="flex flex-col">
                <button class="nes-btn" @click="checkAnswer(false,'25,000')">25,000</button>
                <button class="nes-btn" @click="checkAnswer(true,'22,000')">22,000</button>
                <button class="nes-btn" @click="checkAnswer(false,'17,000')">17,000</button>
              </div>
            </div>
          </div>
          <div v-if="isCorrect === true" class="flex">
            <img class="w-28" src="@/assets/8-bit-lungs.png" alt="rabbit">
            <div class="nes-balloon from-left">
              <p class="typewriter">I bet you are breathing heavily now <i class="nes-icon star"></i></p>
              
            </div>
          </div>
          <div v-else-if="isCorrect === false && isCorrect !== null" class="flex">
            <img class="w-28" src="@/assets/8-bit-lungs.png" alt="rabbit">
            <div class="nes-balloon from-left">
              <p class="typewriter">Wow, you are wrong <i class="nes-icon close"></i></p>
            </div>
          </div>
        </div>
      </div>
</template>