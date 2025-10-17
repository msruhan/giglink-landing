<template>
        <div class="md:col-span-5 relative">
            <div class="tiny-one-icon-item">
                <div v-for="item in datas" :key="item" class="tiny-slide">
                    <div class="m-2 p-3 bg-white dark:bg-slate-900 rounded-lg shadow dark:shadow-gray-800">
                        <router-link :to="{name: 'item-detail', params: {id: item.id}}" class="group relative overflow-hidden rounded-lg">
                            <img :src="item.mainimage" class="rounded-lg" alt="">

                            <span class="absolute bottom-5 start-5">
                                <span class="mb-2 block">
                                    <span class="font-semibold text-white">{{ item.name }}</span>
                                </span>

                                <span class="flex items-center">
                                    <img :src="item.image" class="rounded-full size-8" alt="">
                                    <span class="ms-2 text-[15px] font-medium text-white">{{ item.title }}</span>
                                </span>
                            </span>
                        </router-link>
                    </div>
                </div>
            </div>

            <div
                class="overflow-hidden after:content-[''] after:absolute after:h-14 after:w-14 after:bg-violet-600/10 dark:after:bg-violet-600/30 after:-top-[50px] after:start-[30%] after:-z-1 after:rounded-lg after:animate-[spin_10s_linear_infinite]">
            </div>
        </div><!--end col-->
</template>

<script setup>
import { onMounted } from 'vue'
import { tns } from 'tiny-slider/src/tiny-slider';

const datas = [
    {
        id: 1,
        mainimage: require('../assets/images/items/1.jpg'),
        name: 'Genuine Undead #3902',
        image: require('../assets/images/avatar/1.jpg'),
        title: '@StreetBoy'
    },
    {
        id: 2,
        mainimage: require('../assets/images/items/2.gif'),
        name: 'Windchime #768',
        image: require('../assets/images/avatar/2.jpg'),
        title: '@CutieGirl'
    },
    {
        id: 4,
        mainimage: require('../assets/images/items/3.jpg'),
        name: 'Probably A Label #3277',
        image: require('../assets/images/items/3.gif'),
        title: '@ButterFly'
    },
    {
        id: 6,
        mainimage: require('../assets/images/items/4.jpg'),
        name: 'Probably A Label #1711',
        image: require('../assets/images/avatar/3.jpg'),
        title: '@NorseQueen'
    },
    {
        id: 7,
        mainimage: require('../assets/images/items/5.jpg'),
        name: 'Shibuya Scramble Punks',
        image: require('../assets/images/avatar/4.jpg'),
        title: '@BigBull'
    },
    {
        id: 8,
        mainimage: require('../assets/images/items/6.jpg'),
        name: 'Probably A Label #650',
        image: require('../assets/images/avatar/5.jpg'),
        title: '@Angel'
    },
]

onMounted(() => {
    tns({
        container: '.tiny-one-icon-item',
        items: 1,
        controls: true,
        mouseDrag: true,
        loop: true,
        rewind: true,
        autoplay: true,
        autoplayButtonOutput: false,
        autoplayTimeout: 3000,
        navPosition: "bottom",
        controlsText: ['<i class="mdi mdi-chevron-left "></i>', '<i class="mdi mdi-chevron-right"></i>'],
        nav: false,
        speed: 400,
        gutter: 0,
    });
});

</script>

<style lang="scss" scoped>

</style>