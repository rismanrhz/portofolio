<script setup>
import { experiences } from "../../data/experience";
</script>

<template>
    <section id="experience" class="py-24 bg-slate-50 dark:bg-slate-900">
        <div class="max-w-6xl mx-auto px-6">
            <!-- Title -->
            <div class="text-center mb-20" data-aos="fade-up" data-aos-duration="800">
                <p class="text-pink-600 font-semibold uppercase tracking-widest">Career Journey</p>
                <h2 class="mt-3 text-4xl font-extrabold text-slate-900 dark:text-white">Experience</h2>
                <div class="mx-auto mt-5 h-1 w-24 rounded-full bg-pink-600"></div>
            </div>
        </div>
        <!-- Timeline -->
        <div class="relative">
            <!-- Line -->
            <div class="absolute left-4 top-0 h-full w-1 rounded bg-pink-200 lg:left-1/2 lg:-translate-x-1/2"></div>
            <div
                v-for="(item,index) in experiences"
                :key="item.id"
                class="relative mb-14"
            >
                <!-- Dot -->
                <div class="absolute left-2 h-5 w-5 rounded-full border-4 border-white bg-pink-600 shadow lg:left-1/2 lg:-translate-x-1/2"></div>
                <!-- Card -->
                <div
                    :class="[
                        'ml-12 rounded-2xl bg-white border border-pink-100 p-7 shadow-lg transition-all duration-300 hover:-translate-y-1 hover:shadow-xl dark:bg-slate-800 dark:border-slate-700 lg:w-[45%]',
                        index % 2 === 0
                        ? 'lg:mr-auto lg:ml-0'
                        : 'lg:ml-auto'
                    ]"
                    :data-aos="index % 2 === 0 ? 'fade-right' : 'fade-left'"
                    :data-aos-delay="index * 200"
                    data-aos-duration="900"
                >
                    <span class="inline-block rounded-full bg-blue-100 px-4 py-1 text-sm font-semibold text-pink-600">{{ item.period }}</span>
                    <h3 class="mt-4 text-2xl font-bold text-slate-900 dark:text-white">{{ item.position }}</h3>
                    <h4 class="mt-2 text-lg font-semibold text-pink-600">{{ item.company }}</h4>
                    <p class="mt-5 leading-8 text-slate-600 dark:text-slate-300">{{ item.description }}</p>
                    <div class="mt-6 flex flex-wrap gap-2">
                        <span
                            v-for="(tech,i) in item.technologies"
                            :key="tech"
                            class="rounded-full bg-pink-600 px-4 py-2 text-sm font-medium text-white"
                            data-aos="zoom-in"
                            :data-aos-delay="i * 100"
                        >
                            {{ tech }}
                        </span>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>