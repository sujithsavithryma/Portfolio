<script setup>
import { BsPersonWorkspace } from "vue-icons-plus/bs";
import { ref, onMounted, onBeforeUnmount } from 'vue'
import { AiFillSun, AiFillMoon, AiOutlineUser, AiFillMessage, AiFillGithub, AiFillLinkedin, AiOutlineMenu, AiFillCloseCircle } from "vue-icons-plus/ai";

const activeLink = ref('');
const activeIconClass = 'scale-120 text-[var(--primary)]';
const hoverIconClass = 'group-hover:scale-120 group-hover:text-[var(--primary)]';
const activeTextClass = 'translate-x-2 group-hover:text-[var(--primary)] group-hover:opacity-100';
const hoverTextClass = 'group-hover:translate-x-2 group-hover:text-[var(--primary)] group-hover:opacity-100';
const activeTextColor = 'text-slate-100';
const inactiveTextColor = 'text-slate-600';

const showMenu = ref(false);
const darkMode = ref(true);

function updateActiveSection() {
    const sections = document.querySelectorAll('.section');
    const scrollPosition = window.scrollY + window.innerHeight / 2;
    sections.forEach((section) => {
        const rect = section.getBoundingClientRect();
        const sectionTop = rect.top + window.scrollY;
        const sectionBottom = sectionTop + section.offsetHeight;
        if (scrollPosition >= sectionTop && scrollPosition < sectionBottom && activeLink.value !== section.id) {
            activeLink.value = section.id;
        }
    });
}

function toggleMenu() {
    showMenu.value = !showMenu.value;
}

function toggleDarkMode() {
    darkMode.value = !darkMode.value;
    const elem = document.getElementsByTagName('body')[0];
    if (elem) {
        darkMode.value ? elem.classList.add('dark') : elem.classList.remove('dark');
    }
}

onMounted(() => {
    window.addEventListener('scroll', updateActiveSection);
    const hashs = window.location.hash.split('#');
    if (hashs.length > 1) {
        window.location = ''
    }
    updateActiveSection();
})

onBeforeUnmount(() => {
    window.removeEventListener('scroll', updateActiveSection);
})

</script>
<template>
    <header class="header hidden sticky top-0 lg:flex xl:flex 2xl:flex
    lg:flex-col xl:flex-col 2xl:flex-col w-[140px] h-screen justify-center">
        <ul
            class="relative my-10 pb-10 flex flex-col gap-8 before:border-b-1 before:absolute before:w-10 before:bottom-0 before:left-[-10px]">
            <li>
                <button class="hover:text-[var(--primary)] cursor-pointer" @click.prevent="toggleDarkMode"
                    v-bind:title="darkMode ? 'Change to light theme' : 'Change to dark theme'">
                    <AiFillSun v-if="darkMode" />
                    <AiFillMoon v-else />
                </button>
            </li>

        </ul>

        <nav>
            <ul class="w-max flex flex-col gap-10">
                <li class="group" :class="[activeLink === '' ? activeTextColor : inactiveTextColor]">
                    <a href="#" class="flex items-center gap-1" @click="activeLink = ''">
                        <AiOutlineUser :class="[activeLink === '' ? activeIconClass : hoverIconClass]"
                            class="transition-all" />
                        <span :class="[activeLink === '' ? activeTextClass : hoverTextClass]"
                            class="opacity-0 transition-all">About</span>
                    </a>
                </li>
                <li class="group" :class="[activeLink === 'experience' ? activeTextColor : inactiveTextColor]">
                    <a href="#experience" class="flex items-center gap-1" @click="activeLink = 'experience'">
                        <BsPersonWorkspace :class="[activeLink === 'experience' ? activeIconClass : hoverIconClass]"
                            class="transition-all" />
                        <span :class="[activeLink === 'experience' ? activeTextClass : hoverTextClass]"
                            class="opacity-0 transition-all">Experience</span>
                    </a>
                </li>
                <li class="group" :class="[activeLink === 'contact' ? activeTextColor : inactiveTextColor]">
                    <a href="#contact" class="flex items-center gap-1" @click="activeLink = 'contact'">
                        <AiFillMessage :class="[activeLink === 'contact' ? activeIconClass : hoverIconClass]"
                            class="transition-all" />
                        <span :class="[activeLink === 'contact' ? activeTextClass : hoverTextClass]"
                            class="opacity-0 transition-all">Contact Me</span>
                    </a>
                </li>
            </ul>
        </nav>
        <ul
            class="relative my-10 pt-10 flex flex-col gap-8 before:border-t-1 before:absolute before:w-10 before:top-0 before:left-[-10px]">
            <li class="hover:text-[var(--primary)]">
                <a title="Go to github profile" href="https://www.github.com/sujithsavithryma" target="_blank">
                    <AiFillGithub />
                </a>

            </li>

            <li class="hover:text-[var(--primary)]">
                <a title="Go to linkedIn profile" href="https://www.linkedin.com/in/sujithma/" target="_blank">
                    <AiFillLinkedin />
                </a>
            </li>
        </ul>
    </header>

    <header class="flex sticky top-0 w-full h-[56px] 
        items-center justify-between z-100 px-5 
        bg-zinc-800 shadow-2xl
        lg:hidden xl:hidden 2xl:hidden dark:bg-[var(--bg-color)]">

        <!-- <button @click.prevent="toggleMenu()">
            <AiOutlineMenu  />
        </button>
         -->

        <a href="">
            <img class="h-10" src="../assets/logo.svg" alt="Logo">
        </a>

        <h3 class="text-xl text-slate-200 tracking-widest font-sans">SUJITH M A</h3>

        <div>
            <ul class="relative text-slate-200 flex flex-row gap-3">
                <li>
                    <button class="hover:text-[var(--primary)] cursor-pointer" @click.prevent="toggleDarkMode"
                        v-bind:title="darkMode ? 'Change to light theme' : 'Change to dark theme'">
                        <AiFillSun v-if="darkMode" />
                        <AiFillMoon v-else />
                    </button>
                </li>
                <li class="hover:text-[var(--primary)]">
                    <a href="https://www.github.com/sujithsavithryma" target="_blank">
                        <AiFillGithub />
                    </a>

                </li>

                <li class="hover:text-[var(--primary)]">
                    <a href="https://www.linkedin.com/in/sujithma/" target="_blank">
                        <AiFillLinkedin />
                    </a>
                </li>
            </ul>
        </div>



    </header>

    <!-- <div class="w-[240px] h-screen absolute z-101 bg-gray-800 left-0 top-0 shadow-(--menu-shadow)
        transition-all" :class="showMenu ? '-translate-x-0' : '-translate-x-100'">
            <nav class="flex flex-col gap-10">
                <div class="h-[100px] flex flex-row justify-between items-start px-5 py-5">
                    <h2>Sujith</h2>
                    <button @click.prevent="toggleMenu">
                        <AiFillCloseCircle />
                    </button>
                </div>
                <ul class="w-max flex flex-col gap-10 px-5">
                    <li class="group" :class="[activeLink === '' ? activeTextColor : inactiveTextColor]">
                        <a href="#" class="flex items-center gap-1" @click="activeLink = ''">
                            <span :class="[activeLink === '' ? 'text-emerald-400' : 'hover:text-emerald-400']"
                                class="transition-all opacity-100">About</span>
                        </a>
                    </li>
                    <li class="group" :class="[activeLink === 'experience' ? activeTextColor : inactiveTextColor]">
                        <a href="#experience" class="flex items-center gap-1" @click="activeLink = 'experience'">
                            <span :class="[activeLink === 'experience' ? 'text-emerald-400' : 'hover:text-emerald-400']"
                                class="transition-all opacity-100">Experience</span>
                        </a>
                    </li>
                    <li class="group" :class="[activeLink === 'contact' ? activeTextColor : inactiveTextColor]">
                        <a href="#contact" class="flex items-center gap-1" @click="activeLink = 'contact'">
                            <span :class="[activeLink === 'contact' ? 'text-emerald-400' : 'hover:text-emerald-400']"
                                class="transition-all opacity-100">Contact Me</span>
                        </a>
                    </li>
                </ul>
                
            </nav>
    </div> -->

</template>