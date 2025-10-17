<template>
    <div>
        <span class="fixed blur-[200px] w-[600px] h-[600px] rounded-full top-1/2 start-1/2 ltr:-translate-x-1/2 rtl:translate-x-1/2 -translate-y-1/2 bg-gradient-to-tl from-red-600/20 to-violet-600/20 dark:from-red-600/40 dark:to-violet-600/40"></span>

        <navbar />

        <!-- Start Hero -->
        <section class="relative md:pt-48 pt-36 overflow-hidden">
            <div class="container">
                <div class="grid grid-cols-1 justify-center text-center mt-10">
                    <div class="relative">
                        <div class="relative mb-5">
                            <h1 class="font-bold lg:leading-snug leading-snug text-4xl lg:text-6x">Discover rate <br> collection or <span class="bg-gradient-to-l from-red-600 to-violet-600 text-transparent bg-clip-text">Arts & NFTs</span></h1>

                            <div class="overflow-hidden after:content-[''] after:absolute after:h-10 after:w-10 after:bg-violet-600/10 dark:after:bg-violet-600/30 after:-top-[50px] after:start-[30%] after:-z-1 after:rounded-lg after:animate-[spin_10s_linear_infinite]"></div>

                            <div
                                class="overflow-hidden after:content-[''] after:absolute after:h-10 after:w-10 after:bg-violet-600/20 dark:after:bg-violet-600/40 after:bottom-[0] after:end-[15%] after:-z-1 after:rounded-full after:animate-ping">
                            </div>
                        </div>
                        <p class="text-slate-400 dark:text-white/70 text-lg max-w-xl mx-auto">We are a huge marketplace dedicated to connecting great artists of all Giglink with their fans and unique token collectors!</p>

                        <div class="mt-8">
                            <router-link to="/explore-one" class="btn bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white rounded-full">Explore now</router-link>
                        </div>
                    </div>
                </div><!--end grid-->

                <div class="relative animate-[spin_30s_linear_infinite] -z-1">
                    <span class="after:absolute after:start-0 after:bottom-1/2 after:translate-y-1/2 after:h-2 after:w-8 after:rounded-md after:bg-violet-600/20 relative after:z-10"></span>
                    <span class="after:absolute after:start-0 after:bottom-1/2 after:translate-y-1/2 after:rotate-90 after:h-2 after:w-8 after:rounded-md after:bg-violet-600/20 relative after:z-10"></span>
                </div>
            </div><!--end container-->

            <div class="container md:mt-36 mt-24">

                <div class="md:flex justify-between items-center">
                    <div class="md:w-10/12 md:text-start text-center">
                        <h3 class="md:text-[30px] text-[26px] font-semibold">Top Collections</h3>
                    </div>
                    <div class="md:w-2/12 text-end md:block hidden">
                        <router-link to="/collections" class="btn btn-link text-[16px] font-medium hover:text-violet-600 after:bg-violet-600 duration-500 ease-in-out">See More <i class="uil uil-arrow-right"></i></router-link>
                    </div>
                </div><!--end grid-->
                <collection />
            </div>
        </section><!--end section-->

        <section class="relative md:py-24 py-16">
            <div class="container">
                <div class="grid grid-cols-1 text-center">
                    <h3 class="md:text-[30px] text-[26px] font-semibold">Discover Items</h3>
                </div><!--end grid-->
                <discover :moreitem=true />
            </div>
            <div class="container md:mt-24 mt-16">
                <div class="grid grid-cols-1 text-center">
                    <h3 class="md:text-[30px] text-[26px] font-semibold">Best Creators & Sellers</h3>
                </div><!--end grid-->
                <creators />
            </div>
            <question />
            <getintouch />
        </section>
        <!-- End Hero -->

        <footers />
        <switcher />
    </div>
</template>

<script setup>
import navbar from '@/components/navbar/navbar.vue';
import collection from '@/components/top-collection.vue';
import discover from '@/components/discover-lisensi.vue';
import creators from '@/components/best-creators.vue';
import question from '@/components/question.vue';
import getintouch from '@/components/get-in-touch.vue';
import footers from '@/components/footer/footer.vue';
import switcher from '@/components/switcher.vue'

</script>

<style lang="scss" scoped></style>