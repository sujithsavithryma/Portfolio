<script setup>
import About from './About.vue'
import Experience from './Experience.vue'
import Contact from './Contact.vue'
import Footer from './Footer.vue'
import {ref } from 'vue'

const aboutLoaded = ref(false)

function loaded() {
    aboutLoaded.value = true;
}
</script>
<template>
    <main class="grid lg:min-w-full">
        <About @loaded="loaded" />
        <Experience :aboutLoaded="aboutLoaded" />
        <Contact :aboutLoaded="aboutLoaded"/>
        <Footer :aboutLoaded="aboutLoaded" />
    </main>
</template>