<script setup>
import { FaHouseUser } from "vue-icons-plus/fa";
import { GrContact } from "vue-icons-plus/gr";
import { BsPersonWorkspace } from "vue-icons-plus/bs";
import { ref } from 'vue'

const activeLink = ref('about');
const activeIconClass = 'scale-120';
const hoverIconClass = 'group-hover:scale-120';
const activeTextClass = 'translate-x-2';
const hoverTextClass = 'group-hover:translate-x-2';
const activeTextColor = 'text-slate-100';
const inactiveTextColor = 'text-slate-600';

</script>
<template>
    <header class="sticky top-0 flex flex-col w-[200px] h-full pt-[30%] px-12">
        <nav>
            <ul class="w-max flex flex-col gap-10">
                <li class="group" :class="[activeLink === 'about' ? activeTextColor : inactiveTextColor]">
                    <a href="#about" class="flex items-center gap-1" @click="activeLink = 'about'">
                        <FaHouseUser :class="[activeLink === 'about' ? activeIconClass : hoverIconClass]"
                            class="transition-all" />
                        <span :class="[activeLink === 'about' ? activeTextClass : hoverTextClass]" class="transition-all">About</span>
                    </a>
                </li>
                <li class="group" :class="[activeLink === 'experience' ? activeTextColor : inactiveTextColor]">
                    <a href="#experience" class="flex items-center gap-1" @click="activeLink = 'experience'">
                        <BsPersonWorkspace :class="[activeLink === 'experience' ? activeIconClass : hoverIconClass]" class="transition-all" />
                        <span :class="[activeLink === 'experience' ? activeTextClass : hoverTextClass]" class="transition-all">Experience</span>
                    </a>
                </li>
                <li  class="group" :class="[activeLink === 'contact' ? activeTextColor : inactiveTextColor]">
                    <a href="#contact" class="flex items-center gap-1" @click="activeLink = 'contact'">
                        <GrContact :class="[activeLink === 'contact' ? activeIconClass : hoverIconClass]" class="transition-all" />
                        <span :class="[activeLink === 'contact' ? activeTextClass : hoverTextClass]" class="transition-all">Contact Me</span>
                    </a>
                </li>
            </ul>
        </nav>
    </header>
</template>