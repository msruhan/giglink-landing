<template>
    <div>
        <navbar :navLight="'nav-light'" :logoLight=true />

        <!-- Start Hero -->
        <section class="relative table w-full py-36 bg-[url('../../assets/images/bg/bg1.jpg')] bg-bottom bg-no-repeat">
            <div class="absolute inset-0 bg-gradient-to-b from-transparent to-slate-900"></div>
            <div class="container">
                <div class="grid grid-cols-1 pb-8 text-center mt-10">
                    <h3 class="md:text-3xl text-2xl md:leading-snug tracking-wide leading-snug font-medium text-white">Jasa Remote / Service Online</h3>
                </div><!--end grid-->
            </div><!--end container-->
            
            <div class="grid grid-cols-1 items-center gap-[30px]">
                    <div class="filters-group-wrap text-center">
                        <div class="filters-group">
                            <ul class="mb-0 list-none container-filter-box filter-options">
                                <li class="inline-block font-medium text-base mx-1.5 mb-3 py-1 px-3 cursor-pointer relative text-slate-400 border border-gray-100 dark:border-gray-700 rounded-full transition duration-500"  :class="selectedCategory == 'workshop' ? 'active' : ''" @click="$router.push('/explore-workshop')"><i class="uil uil-browser"></i> Workshop</li>
                                <li class="inline-block font-medium text-base mx-1.5 mb-3 py-1 px-3 cursor-pointer relative text-slate-400 border border-gray-100 dark:border-gray-700 rounded-full transition duration-500" :class="selectedCategory == null ? 'active' : ''" @click="$router.push('/explore-teknisi')"><i class="uil uil-volleyball"></i> Teknisi</li>
                            </ul>
                        </div>
                    </div>
            </div>
        </section><!--end section-->

        <div class="relative">
            <div class="shape absolute start-0 end-0 sm:-bottom-px -bottom-[2px] overflow-hidden z-1 text-white dark:text-slate-900">
                <svg class="w-full h-auto" viewBox="0 0 2880 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M0 48H1437.5H2880V0H2160C1442.5 52 720 0 720 0H0V48Z" fill="currentColor"></path>
                </svg>
            </div>
        </div>
        <!-- End Hero -->

        <section class="relative md:py-24 py-16">
            <div class="container">
                <div class="grid lg:grid-cols-12 md:grid-cols-2 grid-cols-1 gap-[30px]">
                  <searchbar :searchbar=true />
                    <div class="lg:col-span-9">
                      <discover :explore=true />
                      <pagination /> 
                    </div>
                </div>
            </div>
        </section>
        
        <switcher />

        <footers />
    </div>
</template>

<script setup>
import navbar from '@/components/navbar/navbar.vue';
import discover from '@/components/discover-teknisi.vue';
import pagination from '@/components/pagination.vue';
import switcher from '@/components/switcher.vue';
import footers from '@/components/footer/footer.vue';
import searchbar from '@/components/nft-searchbar.vue'

</script>

<style lang="scss" scoped>

</style>