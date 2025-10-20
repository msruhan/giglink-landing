<template>
    <div>
        <navbar :navLight="'nav-light'" :logoLight=true  />
        
        <!-- Start Hero -->
        <!-- Start Hero (Simple for Mobile) -->
        <section class="relative w-full py-20 md:py-36 bg-[url('../../assets/images/bg/bg1.jpg')] md:bg-bottom md:bg-no-repeat bg-none">
            <div class="absolute inset-0 bg-gradient-to-b from-transparent to-slate-900 md:block hidden"></div>
            <div class="container">
                <div class="grid grid-cols-1 pb-4 text-center mt-6 md:pb-8 md:mt-10">
                    <h3 class="text-xl md:text-3xl md:leading-snug tracking-wide leading-snug font-medium text-black">Pusat Produk / Barang</h3>
                </div>
            </div>
        </section>

        <div class="relative md:block hidden">
            <div class="shape absolute start-0 end-0 sm:-bottom-px -bottom-[2px] overflow-hidden z-1 text-white dark:text-slate-900">
                <svg class="w-full h-auto" viewBox="0 0 2880 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M0 48H1437.5H2880V0H2160C1442.5 52 720 0 720 0H0V48Z" fill="currentColor"></path>
                </svg>
            </div>
        </div>
        <!-- End Hero -->

        <section class="relative md:pb-24 pb-16 -mt-16">
            <searchbar />
            <div class="container mt-16">
                <items :items=true />
                <pagination />
            </div>
        </section>

        <switcher />
        
        <footers />
    </div>
</template>

<script setup>
import navbar from '@/components/navbar/navbar.vue';
import searchbar from '@/components/nft-searchbar.vue';
import items from '@/components/discover-marketplace.vue';
import pagination from '@/components/pagination.vue';
import switcher from '@/components/switcher.vue';
import footers from '@/components/footer/footer.vue'

</script>

<style lang="scss" scoped>

</style>