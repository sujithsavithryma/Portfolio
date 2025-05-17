<script setup>
import { ref, TransitionGroup, Transition } from 'vue'
import Appear from './Appear.vue'

const showImage = ref(false);
const arr = ref([]);

for (let i = 1; i < 6; i++) {
    setTimeout(() => {
        arr.value.push(i);
        if (i === 5) {
            showImage.value = true;
        }
    }, 100 * i);
}

</script>
<template>
    <section id="about" class="flex py-54 gap-5 min-h-screen">
        <div class="flex flex-col w-[700px]">

            <TransitionGroup name="fade" tag="div">
                <div class="fade-in-items" v-for="item in arr" :key="item">
                    <h4 v-if="item === 1" class="text-emerald-400 text-xl">Hi, my name is</h4>
                    <h1 v-if="item === 2" class="text-8xl font-bold text-slate-300 mb-5">Sujith</h1>
                    <h2 v-if="item === 3" class="text-2xl font-normal text-slate-300 mb-10">Front-end Engineer</h2>
                    <p v-if="item === 4" class="text-2xl mb-10">I am a passionate engineer who loves to build solid and
                        scalable front-end products.
                        Currently I am Tech Lead at Expian Technologies Bengaluru
                    </p>
                    <div v-if="item === 5">
                        <ul class="ml-5 list-disc text-xl">
                            <li class="pb-2"><b class="text-emerald-400">10 years</b> of experience in front-end technologies</li>
                            <li class="pb-2">Expert in <a href="https://angular.dev/" class="link text-emerald-400 after:bg-emerald-400">Angular</a>; Built a ton of applications</li>
                            <li class="pb-2">Gaining hands-on experience with <a href="https://vuejs.org/" class="link text-emerald-400 after:bg-emerald-400">Vue.js</a>,
                                <a href="https://react.dev/" class="link text-cyan-500 after:bg-cyan-500">React.js</a> and 
                                <a href="https://www.djangoproject.com/" class="link text-green-600 after:bg-green-600">Django</a></li>
                        </ul>
                    </div>
                </div>
            </TransitionGroup>

        </div>
        <div class="w-[400px]">
            <Transition name="slideIn">
                <div v-if="showImage"
                    class="w-[400px] -skew-y-2 hover:-skew-y-0 transition-all rounded-[1vw] shadow-xl/30 shadow-emerald-400">
                    <img class="rounded-[1vw]" src="../assets/Sujith.jpg" alt="Image of Sujith">
                </div>
            </Transition>
        </div>
    </section>
</template>