<script setup>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
</script>

<template>
  <!-- flex-col gap-0
      lg:flex lg:flex-row lg:gap-10 
      xl:flex xl:flex-row xl:gap-15 
      2xl:flex 2xl:flex-row 2xl:gap-40 
      lg:px-10 2xl:px-40  -->
 <div class="mx-auto min-h-screen max-w-[2000px]">
    <div class="lg:px-15 2xl:px-40 grid lg:grid-cols-[140px_1fr] 2xl:grid-cols-[300px_1fr]">
      <Header />
      <Main />
    </div>
 </div>
</template>

<style scoped>

</style>
