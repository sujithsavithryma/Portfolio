<script setup>
import { ref, TransitionGroup, Transition } from 'vue'

const showImage = ref(false);
const arr = ref([]);

const emit = defineEmits(['loaded'])

for (let i = 1; i < 6; i++) {
    setTimeout(() => {
        arr.value.push(i);
        if (i === 5) {
            showImage.value = true;
            emit('loaded')
        }
    }, 100 * i);
}


</script>
<template>
    <section class="section pt-10 sm:pt-20 px-6 lg:px-0 gap-8 lg:w-full">
        <div class="h-full grid grid-cols-[1fr, 1fr] lg:grid-cols-[1fr_400px] lg:min-w-46 gap-5">
            <div class="flex justify-center lg:justify-start about-content">

                <TransitionGroup name="fade" tag="div">
                    <div class="fade-in-items" v-for="item in arr" :key="item">
                        <h4 v-if="item === 1" class="text-[var(--primary)] text-xl text-center lg:text-left tracking-widest">
                            Hello, I am
                        </h4>
                        <h1 v-if="item === 2" class="text-8xl font-bold tracking-wide text-[var(--title-color)] mb-10 text-center lg:text-left">
                            Sujith.
                        </h1>
                        <!-- <h2 v-if="item === 3" class="text-2xl font-normal text-slate-300 mb-10">front end Engineer</h2> -->
                        <p v-if="item === 4" class="text-2xl mb-10 text-center lg:text-left">
                            A passionate engineer
                            who
                            loves to build solid and
                            scalable front end products.
                        </p>
                        <div v-if="item === 5" class="flex justify-center lg:justify-start">
                            <ul class="ml-5 list-disc text-xl ">
                                <li class="pb-2"><b class="text-[var(--primary)]">10 years</b> of experience in front end
                                    technologies.</li>
                                <li class="pb-2">Expert in <a target="_blank" href="https://angular.dev/"
                                        class="link text-[var(--primary)] after:bg-[var(--primary)]">Angular</a>; Built many applications.</li>
                                <li class="pb-2">Gaining hands-on experience with <a target="_blank" href="https://vuejs.org/"
                                        class="link text-[var(--primary)] after:bg-[var(--primary)]">Vue.js</a>,
                                    <a href="https://react.dev/" target="_blank"
                                        class="link text-cyan-500 after:bg-cyan-500">React.js</a>
                                    and
                                    <a href="https://www.djangoproject.com/" target="_blank"
                                        class="link text-green-600 after:bg-green-600">Django.</a>
                                </li>
                            </ul>
                        </div>

                    </div>
                </TransitionGroup>

            </div>
            <div class="flex justify-center about-content pt-3">
                <div class="w-[300px] h-[255px] lg:w-[400px] lg:h-[340px]">
                    <Transition name="slideIn">
                        <div v-if="showImage"
                            class="flex items-center  justify-center w-[300px] h-[255px] lg:w-[400px] lg:h-[340px] awesome-border rounded-[1vw] shadow-xl/20 shadow-emerald-400">
                            <img class="rounded-[1vw] w-[98%]" src="../assets/Sujith.jpg" alt="Image of Sujith">
                        </div>
                    </Transition>
                </div>
    
            </div>
        </div>


    </section>
</template>