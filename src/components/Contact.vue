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

<template>
    <section v-if="showTitle" id="contact" class="section py-10 w-full flex flex-col items-center 
         lg:my-100">
        <h3 class="text-6xl text-emerald-400 mb-10 ">Get In Touch</h3>
        <div class="flex flex-col mb-10 text-center">
            <p class="text-2xl px-10">I'm currently open to new opportunities and ready to join immediately. Whether you
                have
                a role to discuss, suggestions to share, or simply want to connect—feel free to reach out via
                <a class="link text-cyan-400
                    after:bg-cyan-400" href="https://www.linkedin.com/in/sujithma/">LinkedIn</a> or email me directly.
            </p>
        </div>
        <button class="py-4 px-10 border-1 border-emerald-500 rounded-lg 
            text-emerald-400 relative cursor-pointer
            transition-all gradient-before">
            <a href="mailto:sujithma1992@gmail.com">Say Hello</a>

        </button>
    </section>
</template>
