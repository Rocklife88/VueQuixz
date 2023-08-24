<template>
  <div>

<NavMenu/>
<Transition name="route">
  <RouterView/>
</Transition>

  </div>
</template>

<script setup>
import { RouterView } from 'vue-router';
import NavMenu from './components/NavMenu.vue';

</script>

<style scoped>
*{
  font-family: 'Poppins', sans-serif;;
}

.route-enter-from{
  opacity:0;
  transform: translateX(100px)
}

.route-enter-to{
  opacity:1;
  transform: translateX(0);
}

.route-enter-active{
  transition: all 0.4s ease;

}

</style>