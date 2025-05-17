<script setup>
import { BsPersonWorkspace } from "vue-icons-plus/bs";
import { ref, onMounted, onBeforeUnmount } from 'vue'
import { AiOutlineUser, AiFillMessage, AiFillGithub, AiFillLinkedin } from "vue-icons-plus/ai";

const activeLink = ref('');
const activeIconClass = 'scale-120 text-emerald-400';
const hoverIconClass = 'group-hover:scale-120 group-hover:text-emerald-400';
const activeTextClass = 'translate-x-2 group-hover:text-emerald-400 group-hover:opacity-100';
const hoverTextClass = 'group-hover:translate-x-2 group-hover:text-emerald-400 group-hover:opacity-100';
const activeTextColor = 'text-slate-100';
const inactiveTextColor = 'text-slate-600';


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
            <li class="hover:text-emerald-400">
                <a href="https://www.github.com/sujithsavithryma" target="_blank">
                    <AiFillGithub />
                </a>

            </li>

            <li class="hover:text-emerald-400">
                <a href="https://www.linkedin.com/in/sujithma/" target="_blank">
                    <AiFillLinkedin />
                </a>
            </li>
        </ul>
    </header>

    <header class="flex sticky top-0 w-full h-[56px] 
        items-center z-100 px-5 bg-gray-900 shadow-2xl
        lg:hidden xl:hidden 2xl:hidden">
        <a href="">
            <img class="h-10" src="../assets/logo.svg" alt="Logo">
        </a>

        <div class="flex w-full justify-center ">
            <nav class="flex gap-10">
                <ul class="w-max flex gap-10">
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
                <ul class="relative flex flex-row gap-2">
                    <li class="hover:text-emerald-400">
                        <a href="https://www.github.com/sujithsavithryma" target="_blank">
                            <AiFillGithub />
                        </a>

                    </li>

                    <li class="hover:text-emerald-400">
                        <a href="https://www.linkedin.com/in/sujithma/" target="_blank">
                            <AiFillLinkedin />
                        </a>
                    </li>
                </ul>
            </nav>
        </div>

    </header>

</template>