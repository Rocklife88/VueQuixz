<script setup>
import { defineProps, computed } from 'vue';
import { RouterLink } from 'vue-router';

const { quizQuestionLength, numberOfCorrectAnswers } = defineProps(["quizQuestionLength", "numberOfCorrectAnswers"]);

const showResult = computed(() => {
    return numberOfCorrectAnswers
});
</script>

<template>
    <div class="results">
        <p>your Results is:</p>
        <div>
            <h1 class="win" v-if="showResult > 1">{{ showResult }} All right! You did well</h1>
            <h2 class="win" v-else>{{ showResult }} : Not so good </h2>
        </div>


        <RouterLink to="/">
            <button class="button">Back</button>
        </RouterLink>
    </div>
</template>

<style scoped>
.results {
    text-align: center;
    width:300px;
    margin:0 auto;
    padding: 100px 0;
    margin-bottom:5rem;
}

p {
    font-size: 2.4rem;
}

h1 {
    font-size: 3rem;
}
h2{
    font-size:2rem;
}

.button {
    background-color: bisque;
    padding: 0.8rem 2rem;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 1.3rem;
    margin-top: 3rem;
}

.win{
    font-size:2.2rem;
    display:flex;
    justify-content: center;
    align-items:center;

    width:15rem;
    text-align:center;
    margin: 0 auto;
   height:6rem;
    padding:2rem;
    border:2px solid bisque;
    padding:1rem;
}
</style>
