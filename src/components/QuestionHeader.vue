<script setup>
import { defineProps } from 'vue';
const {
  questionStatus,
  barPercentage} = defineProps([
    "questionStatus" ,
    "barPercentage"])

</script>

<template>
    <header>
        <h4>{{questionStatus}}</h4>
        <div class="bar">
          <div :style="{width: barPercentage}" class="completion"></div>
        </div>
        </header>
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
</style>