<template>
  <div class="card" @click="navigateToQuiz">
    <img :src="quiz.img" alt="">
    <div class="card-title">
{{ quiz.name }}
    </div>
    <div class="card-text">
    {{ quiz.questions.length }} questions
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';
import router from '../router';

const {quiz} = defineProps(['quiz'])

const navigateToQuiz = () =>{
  router.push(`/quiz/${quiz.id}`)
}

</script>

<style scoped>
.card{
  width:300px;
  height:300px;
  display:flex;
  flex-direction:column;
  gap:1rem;
  overflow:hidden;
  border:0.7px solid rgba(0, 0, 0, 0.211);
  border-radius:6px;
  padding:1.2rem;
  cursor:pointer;

}

img{
  width:100%;
  height:auto;

}

</style>