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

<template>
    <section v-if="showTitle" id="contact" class="section w-full px-6 flex flex-col items-center lg:items-start lg:pt-40 lg:pb-20">
        <h3 class="text-6xl text-slate-600 mb-10 ">Get In Touch</h3>
        <div class="flex flex-col mb-10 text-center lg:text-left">
            <p class="text-xl lg:px-0">I'm currently open to new opportunities and ready to join immediately. Whether you
                have
                a role to discuss, suggestions to share, or simply want to connect—feel free to reach out via
                <a class="link text-cyan-600
                    after:bg-cyan-400" target="_blank" href="https://www.linkedin.com/in/sujithma/">LinkedIn</a> or email me directly.
            </p>
        </div>
        <button class="py-4 px-10 border-1 border-[var(--primary)] rounded-lg 
            text-[var(--primary)] relative cursor-pointer
            transition-all gradient-before">
            <a target="_blank" href="mailto:sujithma1992@gmail.com">Say Hello</a>
        </button>
    </section>
</template>
