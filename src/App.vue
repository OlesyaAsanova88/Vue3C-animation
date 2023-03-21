<script setup>
import { RouterLink, RouterView } from "vue-router"

</script>

<template>
  
  <header>
    <RouterLink class="r-link" active-class="active" to="/">Home</RouterLink>
    <RouterLink class="r-link" active-class="active" to="/about">About</RouterLink>
  </header> 

  <Transition name="route">
    <RouterView/>
  </Transition>
</template>

<style scoped>
header {
  margin-top: 30px;
  text-align: center;
}
 .r-link{
  margin-left: 30px;
  text-decoration: none;
  color: #282828;
  font-weight: 500;
}
.active {
  font-weight: 600;
  color: teal;
}

.route-enter-from {
  opacity: 0;
  transform: translateX(100px);
}
.route-enter-to {
  opacity: 1;
  transform: translateX(0);
}
.route-enter-active {
  transition: all 0.8s ease;  
}
</style>
