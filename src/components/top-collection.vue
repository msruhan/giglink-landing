<template>
   <div>
        <div class="grid relative grid-cols-1 mt-10">
            <div class="tiny-four-icon-item">
                <div v-for="item in datas" :key="item" class="tiny-slide">
                    <div class="group relative overflow-hidden bg-white dark:bg-slate-900 rounded-lg p-3 shadow dark:shadow-gray-800 ease-in-out duration-500 m-2">
                        <img :src="item.mainimage" class="rounded-lg" alt="">

                        <div class="relative p-4 -mt-14">
                            <div class="relative inline-block">
                                <img :src="item.image" class="h-16 rounded-md shadow-md dark:shadow-gray-800" alt="">
                                <i class="mdi mdi-check-decagram text-emerald-600 text-2xl absolute -bottom-3 -end-2"></i>
                            </div>

                            <div class="mt-3"> 
                                <router-link to="/explore-one" class="font-semibold block text-[18px] hover:text-violet-600">{{item.name}}</router-link>
                                <span class="text-slate-400 mt-1 text-sm"><span class="italic">by</span> <router-link to="/creator-profile" class="text-violet-600 font-medium">{{item.title}}</router-link></span>
                                <span class="text-slate-400 block text-[16px] mt-1">{{item.item}}</span>
                            </div>
                        </div>
                    </div>
                    <!-- End Content -->
                </div>
            </div>
        </div><!--end grid-->
        <div class="grid grid-cols-1 mt-6 md:hidden">
            <div class="text-center">
                <router-link to="/collections" class="btn btn-link text-[16px] font-medium hover:text-violet-600 after:bg-violet-600 duration-500 ease-in-out">See More <i class="uil uil-arrow-right"></i></router-link>
            </div>
        </div><!--end grid-->
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { tns } from 'tiny-slider/src/tiny-slider';


const datas = ref([
    {
        mainimage:  require('../assets/images/items/1.jpg'),
        image: require('../assets/images/avatar/1.jpg'),
        name: 'Digital Collection',
        title: '@CutieGirl',
        item: '25 Items'
    },
    {
        mainimage:  require('../assets/images/items/2.gif'),
        image: require('../assets/images/avatar/2.jpg'),
        name: 'GIF Collection',
        title: '@ButterFly',
        item: '25 Items'
    },
    {
        mainimage:  require('../assets/images/items/3.jpg'),
        image: require('../assets/images/avatar/3.jpg'),
        name: 'Sports Collection',
        title: '@NorseQueen',
        item: '25 Items'
    },
    {
        mainimage:  require('../assets/images/items/4.jpg'),
        image: require('../assets/images/avatar/4.jpg'),
        name: 'Photography Collection',
        title: '@BigBull',
        item: '25 Items'
    },
    {
        mainimage:  require('../assets/images/items/5.jpg'),
        image: require('../assets/images/avatar/5.jpg'),
        name: 'Illustrations Collection',
        title: '@Angel',
        item: '25 Items'
    },
    {
        mainimage:  require('../assets/images/items/6.jpg'),
        image: require('../assets/images/avatar/6.jpg'),
        name: 'Animations Collection',
        title: '@CrazyAnyone',
        item: '25 Items'
    },
]) 



onMounted(() => {
    tns({
        container: '.tiny-four-icon-item',
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
        responsive: {
            1025: {
                items: 4
            },

            992: {
                items: 3
            },

            767: {
                items: 2
            },

            320: {
                items: 1
            },
        },
    });
});
</script>

<style lang="scss" scoped></style>