<template>


    <div v-if="blog" class="grid lg:grid-cols-3 md:grid-cols-2 grid-cols-1 gap-[30px]">
        <div v-for="item in datas" :key="item"
            class="group relative overflow-hidden bg-white dark:bg-slate-900 rounded-md shadow dark:shadow-gray-700 hover:shadow-md transition-all duration-500">
            <img :src="item.image" alt="">

            <div class="relative p-6">
                <div class="absolute start-6 -top-4">
                    <span class="bg-violet-600 text-white text-[12px] px-2.5 py-1 font-semibold rounded-full h-5">{{ item.category }}</span>
                </div>

                <div class="">
                    <div class="flex mb-4">
                        <span class="text-slate-400 text-[16px]"><i class="uil uil-calendar-alt text-slate-900 dark:text-white me-2"></i>{{ item.date}}</span>
                        <span class="text-slate-400 text-[16px] ms-3"><i class="uil uil-clock text-slate-900 dark:text-white me-2"></i>{{ item.time }}</span>
                    </div>

                    <router-link :to="{ name: 'blog-detail', params: { id: item.id } }" class="title text-lg font-medium hover:text-violet-600 duration-500 ease-in-out">{{ item.title }}</router-link>

                    <div class="flex justify-between mt-4">
                        <router-link :to="{ name: 'blog-detail', params: { id: item.id } }" class="btn btn-link text-[16px] font-medium hover:text-violet-600 after:bg-violet-600 duration-500 ease-in-out">Read More <i class="uil uil-arrow-right"></i></router-link>
                        <span class="text-slate-400 text-[16px]">by <router-link to="/creator-profile" class="text-slate-900 dark:text-white hover:text-violet-600 dark:hover:text-violet-600 font-medium">{{item.by }}</router-link></span>
                    </div>
                </div>
            </div>
        </div>
    </div><!--end grid-->


    <div v-else class="container lg:mt-24 mt-16">
        <div class="grid grid-cols-1 pb-8 text-center">
            <h6 v-if="minds" class="text-violet-600 font-medium mb-2">Our Minds</h6>
            <h3 class="mb-4 md:text-3xl text-2xl md:leading-snug leading-snug font-semibold">Latest Blog or News</h3>

            <p class="text-slate-400 max-w-xl mx-auto">We are a huge marketplace dedicated to connecting great artists of all Giglink with their fans and unique token collectors!</p>
        </div><!--end grid-->

        <div class="grid lg:grid-cols-3 md:grid-cols-2 grid-cols-1 mt-8 gap-[30px]">
            <div v-for="item in datas.slice(0, 3)" :key="item" class="group relative overflow-hidden bg-white dark:bg-slate-900 rounded-md shadow dark:shadow-gray-700 hover:shadow-md transition-all duration-500">
                <img :src="item.image" alt="">

                <div class="relative p-6">
                    <div class="absolute start-6 -top-4">
                        <span class="bg-violet-600 text-white text-[12px] px-2.5 py-1 font-semibold rounded-full h-5">{{item.category }}</span>
                    </div>

                    <div class="">
                        <div class="flex mb-4">
                            <span class="text-slate-400 text-[16px]"><i class="uil uil-calendar-alt text-slate-900 dark:text-white me-2"></i>{{ item.date}}</span>
                            <span class="text-slate-400 text-[16px] ms-3"><i class="uil uil-clock text-slate-900 dark:text-white me-2"></i>{{ item.time }}</span>
                        </div>

                        <router-link :to="{ name: 'blog-detail', params: { id: item.id } }" class="title text-lg font-medium hover:text-violet-600 duration-500 ease-in-out">{{ item.title }}</router-link>

                        <div class="flex justify-between mt-4">
                            <router-link :to="{name: 'blog-detail', params: {id: item.id}}" class="btn btn-link text-[16px] font-medium hover:text-violet-600 after:bg-violet-600 duration-500 ease-in-out">Read More <i class="uil uil-arrow-right"></i></router-link>
                            <span class="text-slate-400 text-[16px]">by <router-link to="/creator-profile" class="text-slate-900 dark:text-white hover:text-violet-600 dark:hover:text-violet-600 font-medium">{{item.by}}</router-link></span>
                        </div>
                    </div>
                </div>
            </div>
            <!--end content-->
        </div><!--end grid-->
    </div><!--end container-->
</template>

<script setup>
import { defineProps } from 'vue';

defineProps({
    minds: {
        type: Boolean,
        required: true
    },
    blog: {
        type: Boolean,
        required: true
    },
})

const datas = [
    {
        id: 1,
        image: require('../../assets/images/blog/01.jpg'),
        category: 'Arts',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'Mindfulness Activities for Kids & Toddlers with NFT',
        by: '@StreetBoy'
    },
    {
        id: 2,
        image: require('../../assets/images/blog/02.jpg'),
        category: 'Illustration',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'Save Thousands Of Lives Through This NFT',
        by: '@CutieGirl'
    },
    {
        id: 3,
        image: require('../../assets/images/blog/03.jpg'),
        category: 'Music',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'A place where technology meets craftsmanship',
        by: '@ButterFly'
    },
    {
        id: 4,
        image: require('../../assets/images/blog/04.jpg'),
        category: 'Video',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'NFT Market - A Compact Trike with the Big Benefits',
        by: '@NorseQueen'
    },
    {
        id: 5,
        image: require('../../assets/images/blog/05.jpg'),
        category: 'Games',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'Honoring Black History Month with Toddlers',
        by: '@BigBull'
    },
    {
        id: 6,
        image: require('../../assets/images/blog/06.jpg'),
        category: 'Memes',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'Setting Intentions Instead of Resolutions for 2021',
        by: '@Angel'
    },
    {
        id: 7,
        image: require('../../assets/images/blog/07.jpg'),
        category: 'GIFs',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'Clever Ways to Purchase Extraordinart Items',
        by: '@CrazyAnyone'
    },
    {
        id: 8,
        image: require('../../assets/images/blog/08.jpg'),
        category: 'Video',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'How to Save Money on Baby Essentials for NFT',
        by: '@Princess'
    },
    {
        id: 9,
        image: require('../../assets/images/blog/09.jpg'),
        category: 'Music',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'Liki Trike - A Compact Trike with the Big Benefits',
        by: '@LooserBad'
    },
    {
        id: 10,
        image: require('../../assets/images/blog/10.jpg'),
        category: 'Tech',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'NFT Market - A Compact the Big Benefits',
        by: '@Princess'
    },
    {
        id: 11,
        image: require('../../assets/images/blog/11.jpg'),
        category: 'Arts',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'Behind the Scenes of the creabik App',
        by: '@PandaOne'
    },
    {
        id: 12,
        image: require('../../assets/images/blog/12.jpg'),
        category: 'GIFs',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'Meet fennouni, Product Designer at GitHub',
        by: '@FunnyGuy'
    },
]

</script>

<style lang="scss" scoped></style>