<template>
    <div>
        <navbar />
        <!-- Start -->
        <section class="relative lg:pt-24 pt-[74px] overflow-hidden">
            <div class="container-fluid relative overflow-hidden">
                <div class="absolute top-0 start-0 w-full h-full z-0 pointer-events-none overflow-hidden">
                    <iframe src="https://player.vimeo.com/video/502163294?background=1&autoplay=1&loop=1&byline=0&title=0" class="absolute top-1/2 start-1/2 ltr:-translate-x-1/2 rtl:translate-x-1/2 -translate-y-1/2 w-screen h-[56.25vw] min-h-screen min-w-[177.77vw]"></iframe>
                </div>
                <div class="absolute inset-0 bg-gradient-to-b from-transparent to-slate-900"></div>

                <div class="lg:pt-36 lg:pb-48 pt-24 pb-36 shadow dark:shadow-gray-800">
                    <div class="container">
                        <div class="grid grid-cols-1 justify-center text-center">
                            <div class="relative">
                                <div class="relative mb-5">
                                    <h1 class="font-bold lg:leading-snug leading-snug text-4xl lg:text-6xl text-white">The Place Where any <br> <span class="bg-gradient-to-l from-red-600 to-violet-600 text-transparent bg-clip-text">Technicians</span> Connect, Trade & Grow </h1>
                                </div>
                                <p class="text-white/70 text-lg max-w-xl mx-auto">Marketplace dan Komunitas Teknisi Smartphone Indonesia — Jual alat servis, cari jasa, ikuti workshop, dan diskusi bareng ribuan teknisi aktif!</p>

                                <div class="mt-8">
                                    <router-link to="/explore-one" class="btn bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white rounded-full">Explore Marketplace</router-link>
                                </div>
                            </div>
                        </div><!--end grid-->
                    </div><!--end container-->
                </div><!--end -->
            </div><!--end container fluid-->
        </section><!--end section-->
        <!-- End -->
        <section class="relative md:pb-24 pb-16 -mt-16">
            <searchbar />
            <div class="container md:mt-24 mt-16">
                <desctination></desctination>
            </div>
            
            <collection />

            <auction />

            <div class="container md:mt-24 mt-16">
                <div class="grid grid-cols-1 text-center">
                    <h3 class="mb-4 md:text-3xl text-2xl md:leading-snug leading-snug font-semibold">Creators & Seller</h3>

                    <p class="text-slate-400 max-w-xl mx-auto">We are a huge marketplace dedicated to connecting great artists of all Giglink with their fans and unique token collectors!</p>
                </div>
                <creators />
            </div>  

        </section>

        <footers />
        
        <switcher />
    </div>
</template>

<script setup>
import navbar from '@/components/navbar/navbar.vue';
import searchbar from '@/components/nft-searchbar.vue';
import desctination from '@/components/giglink-destination.vue';
import collection from '@/components/nft-collection.vue';
import auction from '@/components/live-auctions.vue';
import creators from '@/components/nft-creators.vue';
import footers from '@/components/footer/footer.vue';
import switcher from '@/components/switcher.vue'

</script>

<style lang="scss" scoped></style>