<script setup>
import { defineProps, defineEmits } from 'vue';
const {question} = defineProps(['question'])
const emit = defineEmits(["selectOption"])


const emitSelectedOption = (isCorrect) => {
  emit ("selectOption", isCorrect)

}





</script>

<template>

   
          <div class="question-container">
            <div class="question">
      {{question.text}}
            </div>
            <div class="options-container">
              <div v-for="option in question.options" 
              :key="option.id" 
              class="option"
              @click="emitSelectedOption(option.isCorrect)"              >
              <p class="option-label">{{option.label}}</p>
                <div class="option-value">{{option.text}}</div>
              </div>
            </div>
          </div>
</template>

<style scoped>


  h4 {
    font-size: 2rem;
  }
  .bar {
    width: 300px;
    height: 50px;
    border: 3px solid bisque;
  }
  .completion {
    height: 100%;
    width: 0%;
    background-color: bisque;
  }
  .question-container {
    margin-top: 2rem;
  }
  .question {
    font-size: 3.2rem;
    margin-bottom: 20px;
  }
  .option {
    display: flex;
    margin-bottom: 1.8rem;
    cursor: pointer;
    width: 90%; 
    max-width: 700px; 
    padding: 0.5rem;
    background-color: rgba(244, 239, 239);
    border-radius: 5px;
    align-items: center; 
  }
  .option-label {
    background-color: bisque;
    margin-right: 0.5rem;
    padding: 0.2rem 0.5rem;
    border-radius: 5px;
  }
  .option-value {
    flex: 1;
  }
</style>