<template>
    <div class="container md:mt-24 mt-16">
        <div class="grid grid-cols-1 text-center">
            <h3 class="mb-4 md:text-3xl text-2xl md:leading-snug leading-snug font-semibold">Q&A</h3>

            <p class="text-slate-400 max-w-xl mx-auto">We are a huge marketplace dedicated to connecting great artists of all Giglink with their fans and unique token collectors!</p>
        </div><!--end grid-->

        <div class="flex justify-center mt-10">
            <div class="lg:w-2/3">
                <div id="accordion-collapseone" data-accordion="collapse" class="mt-6">
                    <div v-for="item in datas" :key="item" class="relative shadow dark:shadow-gray-800 rounded-md overflow-hidden mt-4 first:mt-4">
                        <h2 class="text-base font-semibold" id="accordion-collapse-heading-1">
                            <button type="button" @click="isActive = isActive === item.id ? null : item.id" :class="item.id === isActive ? 'text-violet-600 bg-gray-50 dark:bg-slate-800' : ''" class="flex justify-between items-center p-5 w-full font-semibold text-start">
                                <span>{{item.title}}</span>
                                <svg :class="item.id === isActive ? 'rotate-180' : ''" class="size-4 shrink-0" fill="currentColor"
                                    viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
                                    <path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd"></path>
                                </svg>
                            </button>
                        </h2>
                        <div id="accordion-collapse-body-1" :class="item.id === isActive ? '' : 'hidden'"  aria-labelledby="accordion-collapse-heading-1">
                            <div class="p-5">
                                <p class="text-slate-400 dark:text-gray-400">{{item.desc}}</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div><!--end grid-->
    </div><!--end container-->
</template>

<script setup>
import { ref } from 'vue';

const isActive = ref(1)

const datas = ref([
    {
        id: 1,
        title: 'How does it work ?',
        desc: 'There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration in some form.',
    },
    {
        id: 2,
        title: 'Do I need a designer to use Giglink ?',
        desc: 'There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration in some form.',
    },
    {
        id: 3,
        title: 'What do I need to do to start selling ?',
        desc: 'There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration in some form.',
    },
    {
        id: 4,
        title: 'What happens when I receive an order ?',
        desc: 'There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration in some form.',
    },
])
</script>

<style lang="scss" scoped></style>