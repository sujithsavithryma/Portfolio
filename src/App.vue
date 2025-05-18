<script setup>
import Header from './components/Header.vue'
import Main from './components/Main.vue'

</script>

<template>
  <div class="mx-auto min-h-screen max-w-[2000px]">
    <div class="lg:px-15 2xl:px-40 grid lg:grid-cols-[140px_1fr] 2xl:grid-cols-[300px_1fr]">
      <Header />
      <Main />
    </div>
  </div>
</template>

<style scoped></style>
