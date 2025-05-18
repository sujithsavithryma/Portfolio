<template>
    <footer class="my-10 pb-2 px-6 lg:pb-10" v-if="showTitle">
        <p class="text-center text-md">
            Coded in <a target="_blank" href="https://code.visualstudio.com/" class="link text-slate-500 font-semibold after:bg-slate-500">Visual Studio Code</a>; Built with 
            <a target="_blank" href="https://vite.dev/" class="link text-slate-500 font-semibold after:bg-slate-500">Vite</a>, 
            <a target="_blank" href="https://vuejs.org/" class="link text-slate-500 font-semibold after:bg-slate-500">Vue.js</a> and 
            <a target="_blank" href="https://tailwindcss.com/" class="link text-slate-500 font-semibold after:bg-slate-500">Tailwind CSS</a>
        </p>
    </footer>
</template>

<script setup>
import { ref, watchEffect } from 'vue'

const props = defineProps(['aboutLoaded']);
const showTitle = ref(false);
watchEffect(() => {
    if (props.aboutLoaded) {
        showTitle.value = true;
    }
})
</script>
