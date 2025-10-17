<template>
        <div v-if="collections" class="grid xl:grid-cols-4 lg:grid-cols-3 md:grid-cols-2 grid-cols-1 gap-[30px]">
            <div v-for="item in datas" :key="item" class="group relative overflow-hidden bg-white dark:bg-slate-900 rounded-lg p-3 shadow hover:shadow-md dark:shadow-gray-800 dark:hover:shadow-gray-800 hover:scale-105 ease-in-out duration-500">
                <img :src="item.mainimage" class="rounded-lg" alt="">

                <div class="relative p-4 -mt-14">
                    <div class="relative inline-block">
                        <img :src="item.image" class="h-16 rounded-md shadow-md dark:shadow-gray-800" alt="">
                        <i class="mdi mdi-check-decagram text-emerald-600 text-2xl absolute -bottom-3 -end-2"></i>
                    </div>

                    <div class="mt-3">
                        <router-link to="/explore-one" class="font-semibold block text-[18px] hover:text-violet-600">{{ item.name }}</router-link>
                        <span class="text-slate-400 mt-1 text-sm"><span class="italic">by</span> <router-link  to="/creator-profile" class="text-violet-600 font-medium">{{ item.by }}</router-link></span>
                        <span class="text-slate-400 block text-[16px] mt-1">{{ item.item }}</span>
                    </div>
                </div>
            </div>
            <!-- End Content -->
        </div><!--end grid-->

        <div v-else class="container md:mt-24 mt-16">
            <div class="grid grid-cols-1 text-center">
                <h3 class="mb-4 md:text-3xl text-2xl md:leading-snug leading-snug font-semibold">Top Collection</h3>
                <p class="text-slate-400 max-w-xl mx-auto">We are a huge marketplace dedicated to connecting great artists of all Giglink with their fans and unique token collectors!</p>
            </div><!--end grid-->

            <div class="grid xl:grid-cols-4 lg:grid-cols-3 md:grid-cols-2 grid-cols-1 mt-12 gap-[30px]">
                <div v-for="item in datas" :key="item" class="group relative overflow-hidden bg-white dark:bg-slate-900 rounded-lg p-3 shadow hover:shadow-md dark:shadow-gray-800 dark:hover:shadow-gray-800 hover:scale-105 ease-in-out duration-500">
                    <img :src="item.mainimage" class="rounded-lg" alt="">

                    <div class="relative p-4 -mt-14">
                        <div class="relative inline-block">
                            <img :src="item.image" class="h-16 rounded-md shadow-md dark:shadow-gray-800" alt="">
                            <i class="mdi mdi-check-decagram text-emerald-600 text-2xl absolute -bottom-3 -end-2"></i>
                        </div>

                        <div class="mt-3">
                            <router-link to="/explore-one" class="font-semibold block text-[18px] hover:text-violet-600">{{ item.name }}</router-link>
                            <span class="text-slate-400 mt-1 text-sm"><span class="italic">by</span> <router-link to="/creator-profile" class="text-violet-600 font-medium">{{ item.by }}</router-link></span>
                            <span class="text-slate-400 block text-[16px] mt-1">{{ item.item }}</span>
                        </div>
                    </div>
                </div>
                <!-- End Content -->
            </div><!--end grid-->
        </div><!--end container-->
</template>

<script setup>
import { defineProps } from 'vue';

defineProps({
    collections:{
        type: Boolean,
        required: true
    }
})

const datas = [
    {
        mainimage: require('../assets/images/items/1.jpg'),
        image: require('../assets/images/avatar/1.jpg'),
        name: 'Digital Collection',
        by: '@CutieGirl',
        item: '25 Items'
    },
    {
        mainimage: require('../assets/images/items/2.gif'),
        image: require('../assets/images/avatar/2.jpg'),
        name: 'GIF Collection',
        by: '@ButterFly',
        item: '25 Items'
    },
    {
        mainimage: require('../assets/images/items/3.jpg'),
        image: require('../assets/images/avatar/3.jpg'),
        name: 'Sports Collection',
        by: '@NorseQueen',
        item: '25 Items'
    },
    {
        mainimage: require('../assets/images/items/4.jpg'),
        image: require('../assets/images/avatar/4.jpg'),
        name: 'Photography Collection',
        by: '@BigBull',
        item: '25 Items'
    },
    {
        mainimage: require('../assets/images/items/5.jpg'),
        image: require('../assets/images/avatar/5.jpg'),
        name: 'Illustrations Collection',
        by: '@Angel',
        item: '25 Items'
    },
    {
        mainimage: require('../assets/images/items/6.jpg'),
        image: require('../assets/images/avatar/6.jpg'),
        name: 'Animations Collection',
        by: '@CrazyAnyone',
        item: '25 Items'
    },
    {
        mainimage: require('../assets/images/items/7.jpg'),
        image: require('../assets/images/avatar/7.jpg'),
        name: 'Virtual Reality Collection',
        by: '@Princess',
        item: '25 Items'
    },
    {
        mainimage: require('../assets/images/items/8.gif'),
        image: require('../assets/images/avatar/8.jpg'),
        name: 'Cartoon Collection',
        by: '@LooserBad',
        item: '25 Items'
    },
]

</script>

<style lang="scss" scoped></style>