<script setup>
import Question from '../../components/Question.vue'
import QuestionHeader from '../../components/QuestionHeader.vue'
import Result from '../../components/Result.vue'
import quizData from '../../data/quizData.json'
import { useRoute } from 'vue-router'


import { ref,computed} from 'vue'
import ResultVue from '../../components/Result.vue'

const quizzes = ref(quizData)
const route = useRoute()

const quizId = parseInt(route.params.id)
const quiz = quizzes.value.find(quiz => quiz.id === quizId)
const currentQuestionIndex = ref(0)
const numberOfCorrectAnswers=ref(0)
const showResults =ref(false)


const questionStatus = computed(() => {
 return `${currentQuestionIndex.value}/${quiz.questions.length}`
})

const barPercentage = computed(() => {
  return `${((currentQuestionIndex.value) / quiz.questions.length) * 100}%`
})

const onOptionSelected = (isCorrect) =>{
if(isCorrect){
  numberOfCorrectAnswers.value++;
} if (quiz.questions.length -1 === currentQuestionIndex.value){
  showResults.value=true
}
currentQuestionIndex.value++;
}


</script>

<template>
  <div class="container">
    <div class="quiz-view">
      <div>
        <QuestionHeader 
        :questionStatus="questionStatus"
        :barPercentage="barPercentage"
        />
      </div>
      <div>
        <Question 
        v-if="!showResults"
        :question="quiz.questions[currentQuestionIndex]"
         @selectOption="onOptionSelected" />
         <Result 
         v-else
         :quizQuestionLength="quiz.questions.length"
         :numberOfCorrectAnswers="numberOfCorrectAnswers"/>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 1100px;
  padding:0.5rem;
  margin: 0 auto;
}

.quiz-view {
  margin-top: 2.5rem;
}


</style>
