<script setup>
import { FaHouseUser } from "vue-icons-plus/fa";
import { GrContact } from "vue-icons-plus/gr";
import { BsPersonWorkspace } from "vue-icons-plus/bs";
import { ref, onMounted, onBeforeUnmount } from 'vue'

const activeLink = ref('');
const activeIconClass = 'scale-120';
const hoverIconClass = 'group-hover:scale-120 group-hover:text-emerald-400';
const activeTextClass = 'translate-x-2 group-hover:opacity-100';
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
                        <FaHouseUser :class="[activeLink === '' ? activeIconClass : hoverIconClass]"
                            class="transition-all" />
                        <span :class="[activeLink === '' ? activeTextClass : hoverTextClass]" class="opacity-0 transition-all">About</span>
                    </a>
                </li>
                <li class="group" :class="[activeLink === 'experience' ? activeTextColor : inactiveTextColor]">
                    <a href="#experience" class="flex items-center gap-1" @click="activeLink = 'experience'">
                        <BsPersonWorkspace :class="[activeLink === 'experience' ? activeIconClass : hoverIconClass]" class="transition-all" />
                        <span :class="[activeLink === 'experience' ? activeTextClass : hoverTextClass]" class="opacity-0 transition-all">Experience</span>
                    </a>
                </li>
                <li  class="group" :class="[activeLink === 'contact' ? activeTextColor : inactiveTextColor]">
                    <a href="#contact" class="flex items-center gap-1" @click="activeLink = 'contact'">
                        <GrContact :class="[activeLink === 'contact' ? activeIconClass : hoverIconClass]" class="transition-all" />
                        <span :class="[activeLink === 'contact' ? activeTextClass : hoverTextClass]" class="opacity-0 transition-all">Contact Me</span>
                    </a>
                </li>
            </ul>
        </nav>
    </header>

    <header class="header flex sticky top-0 w-full h-[56px] 
        items-center justify-center z-100  bg-gray-900 shadow-2xl
        lg:hidden xl:hidden 2xl:hidden">
        <nav>
            <ul class="w-max flex gap-10">
                <li class="group" :class="[activeLink === '' ? activeTextColor : inactiveTextColor]">
                    <a href="#" class="flex items-center gap-1" @click="activeLink = ''">
                        <FaHouseUser :class="[activeLink === '' ? activeIconClass : hoverIconClass]"
                            class="transition-all hidden" />
                        <span :class="[activeLink === '' ? activeTextClass : hoverTextClass]" class="transition-all">About</span>
                    </a>
                </li>
                <li class="group" :class="[activeLink === 'experience' ? activeTextColor : inactiveTextColor]">
                    <a href="#experience" class="flex items-center gap-1" @click="activeLink = 'experience'">
                        <BsPersonWorkspace :class="[activeLink === 'experience' ? activeIconClass : hoverIconClass]" class="transition-all hidden" />
                        <span :class="[activeLink === 'experience' ? activeTextClass : hoverTextClass]" class="transition-all">Experience</span>
                    </a>
                </li>
                <li  class="group" :class="[activeLink === 'contact' ? activeTextColor : inactiveTextColor]">
                    <a href="#contact" class="flex items-center gap-1" @click="activeLink = 'contact'">
                        <GrContact :class="[activeLink === 'contact' ? activeIconClass : hoverIconClass]" class="transition-all hidden" />
                        <span :class="[activeLink === 'contact' ? activeTextClass : hoverTextClass]" class="transition-all">Contact Me</span>
                    </a>
                </li>
            </ul>
        </nav>
    </header>

</template>