<script setup>
import { ref } from 'vue'

const workExperience = [
    {
        id: 1,
        designation: 'Tech Lead',
        organization: 'Expian Technologies Pvt Ltd (The Scalers)',
        url: 'https://thescalers.com/',
        period: 'May 2023 - May 2025',
        description: 'After 3 years of consistent contribution, I was promoted to Tech Lead for the same client. In this role, I led the development of new applications and oversaw the maintenance and enhancement of existing systems.',
        points: [
            "Designed and developed more than 10 web applications",
            "Significantly improved the theme library by refactoring code and enhancing overall code quality."
        ],
        skillSet: ['Angular', 'Angular Material', 'Ngx-Translate', 'NgRx', 'Typescript']
    },
    {
        id: 2,
        designation: 'Senior Engineer - Frontend',
        organization: 'Expian Technologies Pvt Ltd (The Scalers)',
        url: 'https://thescalers.com/',
        period: 'Mar 2020 - May 2023',
        description: 'Started working with a major French retail company, where I performed a comprehensive audit of the front-end codebase. I uncovered key architectural and performance flaws, then redesigned and implemented a robust, optimized structure that served as the foundation for future development.',
        points: [
            "Designed and developed more than 10 web applications.",
            "Designed, developed and implemented a reusable theme library using Angular and Angular Material, resulting in a 40% reduction in development time across multiple projects.",
            "Integrated multilingual support across all applications to enhance accessibility and user experience.",
            "Externalized configuration files to decouple configuration parameters from the application code, improving flexibility and ease of environment-specific deployments.",
            "Collaborated on the creation of a CI/CD pipeline, streamlining deployment processes."
        ],
        skillSet: ['Angular', 'Angular Material', 'Ngx-Translate', 'Typescript', 'Architecture',]
    },
    {
         id: 3,
        designation: 'Front end Developer',
        organization: 'Expian Technologies Pvt Ltd (The Scalers)',
        url: 'https://thescalers.com/',
        period: 'Oct 2018 - Feb 2020',
        description: 'Developed a major client application (Vault) and contributed to other two major client applications (Analytics, Comply) for <a class="link text-cyan-400 after:bg-cyan-400" href="https://taxbackinternational.com/" > Taxback International <a/>, an Irish-based organization specializing in VAT compliance, reclamation, and consultancy.',
        points: [
            "Contributes to building a reusable theme library using Angular.",
        ],
        skillSet: ['Angular', 'Angular Material', 'Typescript']
    },
    {
        id: 4,
        designation: 'Software Engineer',
        organization: 'Thinkpalm Technologies Pvt Ltd',
        url: 'https://thinkpalm.com/',
        period: 'Feb 2018 - Oct 2018',
        description: 'Designed and implemented the core architecture for Angular applications, ensuring maintainability and scalability, while mentoring junior team members.',
        points: [
            'Designed and led the development of a scalable Angular web application from the ground up, establishing a solid architectural foundation and best practices.',
            'Mentored junior developers, providing guidance on best practices, code quality, and Angular development techniques.'
        ],
        skillSet: ['Angular', 'Angular Material', 'Ngx-Translate', 'Typescript', 'Architecture']
    },
    {
        id: 5,
        designation: 'Senior Engineer',
        organization: 'Codetok Technologies Pvt Ltd',
        url: '',
        period: 'Feb 2015 - Jan 2018',
        description: 'I was the first employee at Codetok, where I started my front-end journey and picked up Angular from the ground up.',
        points: [
            'Actively contributed to the development and deployment of Angular-based web applications.',
            'Designed, built, and launched cross-platform mobile applications using the Ionic framework.',
            'Led and managed a team of three developers, providing technical guidance and project coordination.',
            'Built and deployed a backend service with Django REST Framework and managed deployment on AWS.'
        ],
        skillSet: ['Angular', 'Angular Material', 'Ngx-Translate', 'Typescript', 'Ionic', 'Javascript', 'Django']
    }
];

</script>
<template>
    <section id="experience" class="py-20">
        <h3 class="text-3xl text-emerald-400 mb-10 text-center">Work Experience</h3>
        <div class="px-10">
            <ul
                class="relative before:absolute before:top-[10px] before:left-[0] before:border-l-1  before:border-emerald-800 before:h-full ">

                <li v-for="work of workExperience" :key="work.id"
                    class="relative pl-10 before:absolute before:top-[6px] before:left-[-12px] before:h-6 before:w-6 before:border-1 before:border-emerald-800 before:bg-gray-900 before:rounded-full">
                    <div class="flex flex-col gap-1 mb-10">
                        <h4 class="text-2xl font-semibold text-slate-300">{{ work.designation }}</h4>
                        <div class="flex flex-col gap-2 mb-2">
                            <a class="link text-emerald-400 text-lg after:bg-emerald-400" v-if="work.url" :href="work.url">
                                {{ work.organization }}
                            </a>
                            <a class="text-emerald-400 text-lg" v-else> {{ work.organization }}</a>
                            <h5
                                class="relative pl-5 text-slate-500 text-md before:absolute before:left-[0] before:top-[8px] before:h-2 before:w-2 before:bg-slate-500 before:rounded-full">
                                {{ work.period }}</h5>
                        </div>
                        <p class="mb-2" v-html="work.description"></p>
                        <ul class="pl-10 list-disc mb-4 flex flex-col gap-2">
                            <li v-for="point of work.points">{{ point }}</li>
                        </ul>
                        <ul class="flex flex-wrap gap-2">
                            <li class="px-4 py-2 
                                border-1 rounded-lg text-xs hover:bg-slate-600 cursor-pointer"
                                v-for="skill of work.skillSet">{{ skill }}</li>
                        </ul>
                    </div>
                </li>
            </ul>
        </div>
    </section>
</template>