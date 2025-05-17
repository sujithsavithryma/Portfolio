<template>
    <footer class="my-10 pb-10" v-if="showTitle">
        <p class="text-center text-slate-500 text-md">
            Coded in <a target="_blank" href="https://code.visualstudio.com/" class="link text-slate-300 font-semibold after:bg-emerald-400">Visual Studio Code</a>; Built with 
            <a target="_blank" href="https://vite.dev/" class="link text-slate-300 font-semibold after:bg-emerald-400">Vite</a>, 
            <a target="_blank" href="https://vuejs.org/" class="link text-slate-300 font-semibold after:bg-emerald-400">Vue.js</a> and 
            <a target="_blank" href="https://tailwindcss.com/" class="link text-slate-300 font-semibold after:bg-emerald-400">Tailwind CSS</a>
        </p>
    </footer>
</template>

<script setup>
import { ref, defineProps, watchEffect } from 'vue'

const props = defineProps(['aboutLoaded']);
const showTitle = ref(false);
watchEffect(() => {
    if (props.aboutLoaded) {
        showTitle.value = true;
    }
})
</script>
