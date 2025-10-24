<template>
    <div>
        <navbar :navLight="'nav-light'" :logoLight=true  />
        
        <!-- Start Hero -->
        <section class="relative w-full py-20 md:py-36 bg-[url('../../assets/images/bg/bg1.jpg')] md:bg-bottom md:bg-no-repeat bg-none">
            <div class="absolute inset-0 bg-gradient-to-b from-transparent to-slate-900 md:block hidden"></div>
            <div class="container">
                <div class="grid grid-cols-1 pb-4 text-center mt-6 md:pb-8 md:mt-10">
                    <h3 class="text-xl md:text-3xl md:leading-snug tracking-wide leading-snug font-medium text-black">Pusat Software / Lisensi</h3>
                </div>
            </div>
                <div class="grid grid-cols-1 items-center gap-[30px]">
                    <div class="filters-group-wrap text-center">
                        <div class="filters-group">
                            <ul class="mb-0 list-none container-filter-box filter-options">
                                <li class="inline-block font-medium text-base mx-1.5 mb-3 py-1 px-3 cursor-pointer relative text-slate-400 border border-gray-100 dark:border-gray-700 rounded-full transition duration-500"  :class="selectedCategory == 'product' ? 'active' : ''" @click="$router.push('/explore-marketplace')"><i class="uil uil-browser"></i> Produk</li>
                                <li class="inline-block font-medium text-base mx-1.5 mb-3 py-1 px-3 cursor-pointer relative text-slate-400 border border-gray-100 dark:border-gray-700 rounded-full transition duration-500" :class="selectedCategory == null ? 'active' : ''" @click="$router.push('/explore-lisensi')"><i class="uil uil-volleyball"></i> Lisensi</li>
                            </ul>
                        </div>
                    </div>
                </div>
        </section>


        <div class="relative">
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
        
        <!-- <footers /> -->
    </div>
</template>

<script setup>
import navbar from '@/components/navbar/navbar.vue';
import searchbar from '@/components/nft-searchbar.vue';
import items from '@/components/discover-lisensi.vue';
import pagination from '@/components/pagination.vue';
import switcher from '@/components/switcher.vue';
import footers from '@/components/footer/footer.vue'

</script>

<style lang="scss" scoped>

</style>