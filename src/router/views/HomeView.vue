<script setup>
import { ref, watch } from 'vue';
import quizData from '../../data/quizData.json';
import Card from '../../components/Card.vue';
import gsap from 'gsap';

const quizzes = ref(quizData);
const search = ref('');

watch(search, () => {
  quizzes.value = quizData.filter(quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()));
});

//enter to
const beforeEnter = el => {
  el.style.opacity = 0;
  el.style.transform = 'translateY(-50px)';
};

//enter-active
const enter = el => {
  gsap.to(el, {
    y: 0,
    opacity: 1,
    duration: 0.3,
    delay:el.dataset.index *0.3
  });
};
</script>

<template>
  <div class="container">
    <div class="input-box">
      <input v-model="search" type="text" placeholder="search..." />
    </div>
    <div class="card-container">
      <TransitionGroup 
      appear 
      @before-enter="beforeEnter" 
       @enter="enter">
        <Card 
        v-for="(quiz, index) in quizzes" 
        :key="quiz.id" 
        :quiz="quiz" 
        :data-index="index"/>
      </TransitionGroup>
    </div>
  </div>
</template>


<style  scoped>
.container {
  max-width: 1100px;
  margin: 0 auto;
}

.card-container {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap:1rem;

  margin-bottom:1.6rem;

}

.input-box{
  margin-bottom:3rem;
}



input[type="text"]{
  padding:0.7rem;
  border-radius:5px;
  font-size:1rem;
  border:0.8px solid black;
}





</style>