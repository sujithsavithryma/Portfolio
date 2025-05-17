<script setup>
import About from './About.vue'
import Experience from './Experience.vue'
import Contact from './Contact.vue'
import {ref } from 'vue'

const aboutLoaded = ref(false)

function loaded() {
    console.log('loaded')
    aboutLoaded.value = true;
}
</script>
<template>
    <main class="flex flex-col sm:items-center ">
        <About @loaded="loaded" />
        <Experience :aboutLoaded="aboutLoaded" />
        <Contact :aboutLoaded="aboutLoaded"/>
    </main>
</template>