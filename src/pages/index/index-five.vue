<template>
    <div>
        <navbar />
        <!-- Start -->
        <section class="relative pt-24 overflow-hidden">
            <div class="container-fluid relative">
                <div class="grid grid-cols-1">
                    <div class="slider relative overflow-hidden m-auto mb-4 before:content-[''] before:absolute before:top-0 before:start-0 before:z-2 after:content-[''] after:absolute after:top-0 after:end-0 after:z-2">
                        <div class="slide-track flex items-center">
                            <div v-for="item in images" :key="item" class="slide h-auto md:w-[360px] w-72 mx-2">
                                <div class="group relative overflow-hidden rounded-lg shadow dark:shadow-gray-800">
                                    <img :src="item.image" class="rounded-lg shadow-md dark:shadow-gray-700 group-hover:scale-110 transition-all duration-500" alt="">
                                    <div class="absolute -bottom-20 group-hover:bottom-1/2 group-hover:translate-y-1/2 start-0 end-0 mx-auto text-center transition-all duration-500">
                                        <router-link :to="{ name: 'item-detail', params: { id: item.id } }" class="btn btn-sm rounded-full bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white"><i class="mdi mdi-gavel"></i> Bid Now</router-link>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div><!--end slider-->

                    <div class="slider2 relative overflow-hidden m-auto before:content-[''] before:absolute before:top-0 before:start-0 before:z-2 after:content-[''] after:absolute after:top-0 after:end-0 after:z-2">
                        <div class="slide-track flex items-center">
                            <div v-for="(item, index) in images2" :key="index" class="slide h-auto md:w-[360px] w-72 mx-2">
                                <div class="group relative overflow-hidden rounded-lg shadow dark:shadow-gray-800">
                                    <img :src="item.image" class="rounded-lg shadow-md dark:shadow-gray-700 group-hover:scale-110 transition-all duration-500" alt="">

                                    <div class="absolute -bottom-20 group-hover:bottom-1/2 group-hover:translate-y-1/2 start-0 end-0 mx-auto text-center transition-all duration-500">
                                        <router-link :to="{ name: 'item-detail', params: { id: item.id } }" class="btn btn-sm rounded-full bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white"><i class="mdi mdi-gavel"></i> Bid Now</router-link>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div><!-- end slider2 -->
                </div><!--end grid-->
            </div><!--end container-->
        </section><!--end section-->
        <!-- End -->
        <section class="relative md:py-24 py-16">
            <div class="container">
                <div class="grid grid-cols-1 text-center">
                    <h3 class="mb-4 md:text-3xl text-2xl md:leading-snug leading-snug font-semibold">Best Creators & Sellers</h3>
                    <p class="text-slate-400 max-w-xl mx-auto">We are a huge marketplace dedicated to connecting great artists of all Giglink with their fans and unique token collectors!</p>
                </div><!--end grid-->
                <creators />
            </div>
            <collection />
            <auction />
            <question />
        </section>
        <footers />
        <switcher />
        </div>
</template>

<script setup>
import navbar from '@/components/navbar/navbar.vue';
import creators from '@/components/best-creators.vue';
import collection from '@/components/nft-collection.vue';
import auction from '@/components/live-auctions.vue';
import question from '@/components/question.vue';
import footers from '@/components/footer/footer.vue';
import switcher from '@/components/switcher.vue'

const images = [
    {
        id: 13,
        image: require('../../assets/images/blog/01.jpg'),
    },
    {
        id: 14,
        image: require('../../assets/images/blog/03.jpg'),
    },
    {
        id: 15,
        image: require('../../assets/images/blog/05.jpg'),
    },
    {
        id: 16,
        image: require('../../assets/images/blog/07.jpg'),
    },
    {
        id: 17,
        image: require('../../assets/images/blog/09.jpg'),
    },
    {
        id: 18,
        image: require('../../assets/images/blog/11.jpg'),
    },
    {
        id: 19,
        image: require('../../assets/images/blog/12.jpg'),
    },
    {
        id: 20,
        image: require('../../assets/images/blog/14.jpg'),
    },
    {
        id: 21,
        image: require('../../assets/images/blog/16.jpg'),
    },
    {
        id: 22,
        image: require('../../assets/images/blog/18.jpg'),
    },
    {
        id: 23,
        image: require('../../assets/images/blog/20.jpg'),
    },
    {
        id: 24,
        image: require('../../assets/images/blog/22.jpg'),
    },
    {
        id: 25,
        image: require('../../assets/images/blog/24.jpg'),
    },
    {
        id: 26,
        image: require('../../assets/images/blog/26.jpg')
    }]


const images2 = [
    {
        id: 27,
        image: require('../../assets/images/blog/02.jpg'),
    },
    {
        id: 28,
        image: require('../../assets/images/blog/04.jpg'),
    },
    {
        id: 29,
        image: require('../../assets/images/blog/06.jpg'),
    },
    {
        id: 30,
        image: require('../../assets/images/blog/08.jpg'),
    },
    {
        id: 31,
        image: require('../../assets/images/blog/10.jpg'),
    },
    {
        id: 32,
        image: require('../../assets/images/blog/13.jpg'),
    },
    {
        id: 33,
        image: require('../../assets/images/blog/15.jpg'),
    },
    {
        id: 34,
        image: require('../../assets/images/blog/17.jpg'),
    },
    {
        id: 35,
        image: require('../../assets/images/blog/19.jpg'),
    },
    {
        id: 36,
        image: require('../../assets/images/blog/21.jpg'),
    },
    {
        id: 37,
        image: require('../../assets/images/blog/23.jpg'),
    },
    {
        id: 38,
        image: require('../../assets/images/blog/25.jpg'),
    },
    {
        id: 39,
        image: require('../../assets/images/blog/01.jpg'),
    },
    {
        id: 40,
        image: require('../../assets/images/blog/05.jpg')
    },
]

</script>

<style lang="scss" scoped></style>