<template>
    <div class="bg-[#f4f4f4] text-[#1a1a1a] min-h-screen">
        <navbar :navLight="'nav-dark'" :logoLight=true />

        <!-- Start Hero -->
        <section class="relative md:pt-48 pt-36 overflow-hidden">
            <div class="container hidden sm:block">
                <div class="grid grid-cols-1 justify-center text-center mt-10">
                    <div class="relative">
                        <div class="relative mb-5">
                            <h1
                                class="text-5xl md:text-6xl font-extrabold tracking-tight text-gray-900 mb-6 leading-tight font-inter"
                            >
                                <span class="text-gray-900">Temukan Workshop / Tempat Service</span> <span class="text-emerald-500">Terbaik di Kota Anda.</span>
                            </h1>
                        </div>
                        <p class="text-[#555] text-lg max-w-xl mx-auto font-inter">Temukan tempat service terpercaya untuk konsultasi dan perbaikan perangkat Anda dengan mudah, cepat dan aman!</p>
                    </div>
                </div>
                <div class="relative animate-[spin_30s_linear_infinite] -z-1">
                    <span class="after:absolute after:start-0 after:bottom-1/2 after:translate-y-1/2 after:h-2 after:w-8 after:rounded-md after:bg-violet-600/20 relative after:z-10"></span>
                    <span class="after:absolute after:start-0 after:bottom-1/2 after:translate-y-1/2 after:rotate-90 after:h-2 after:w-8 after:rounded-md after:bg-violet-600/20 relative after:z-10"></span>
                </div>
            </div>
            <!-- Filter Tabs -->
            <div class="grid grid-cols-1 items-center gap-[30px] mb-10 mt-0 sm:mt-10">
                <div class="filters-group-wrap text-center">
                    <div class="filters-group">
                        <ul class="mb-0 list-none container-filter-box filter-options">
                            <li
                                class="inline-block font-medium text-base mx-1.5 mb-3 py-2 px-4 cursor-pointer relative rounded-full transition duration-500 font-inter"
                                :class="selectedCategory == null 
                                    ? 'bg-[#1a1a1a] text-white' 
                                    : 'text-gray-700 bg-white border border-gray-200 shadow-sm'"
                                @click="$router.push('/explore-workshop')"
                            >
                                <i class="uil uil-browser"></i> Workshop
                            </li>
                            <li
                                class="inline-block font-medium text-base mx-1.5 mb-3 py-2 px-4 cursor-pointer relative rounded-full transition duration-500"
                                :class="selectedCategory == 'teknisi'
                                    ? 'bg-[#ff3d00] text-white'
                                    : 'text-gray-700 bg-white border border-gray-200 shadow-sm'"
                                @click="$router.push('/explore-teknisi')"
                            >
                                <i class="uil uil-volleyball" :class="selectedCategory == 'teknisi' ? 'text-white' : ''"></i> Teknisi
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>
        <!-- End Hero -->

        <discover :explore=true />
        <pagination /> 
        
        <switcher />
        <!-- <footers /> -->
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
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap');

.font-inter {
  font-family: 'Inter', sans-serif;
}

.shadow-md {
  box-shadow: 0 6px 18px rgba(0, 0, 0, 0.05);
}

.ring-gray-100 {
  --tw-ring-color: rgba(0, 0, 0, 0.05);
}
</style>