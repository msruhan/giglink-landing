<template>
    <div>
        <navbar :navLight="'nav-dark'" :logoLight=true  />
        
              <!-- Start Hero -->
       <section class="relative md:pt-48 pt-36 overflow-hidden">
        <div class="container hidden sm:block">
                <div class="grid grid-cols-1 justify-center text-center mt-10">
                    <div class="relative">
                        <div class="relative mb-5">
                            <h1 class="font-bold lg:leading-snug leading-snug text-4xl lg:text-6x">Pusat Software / License <br> untuk Kebutuhan <span class="bg-gradient-to-l from-red-600 to-violet-600 text-transparent bg-clip-text">Perangkat Anda</span></h1>

                            <div class="overflow-hidden after:content-[''] after:absolute after:h-10 after:w-10 after:bg-violet-600/10 dark:after:bg-violet-600/30 after:-top-[50px] after:start-[30%] after:-z-1 after:rounded-lg after:animate-[spin_10s_linear_infinite]"></div>

                            <div
                                class="overflow-hidden after:content-[''] after:absolute after:h-10 after:w-10 after:bg-violet-600/20 dark:after:bg-violet-600/40 after:bottom-[0] after:end-[15%] after:-z-1 after:rounded-full after:animate-ping">
                            </div>
                        </div>
                        <p class="text-slate-400 dark:text-white/70 text-lg max-w-xl mx-auto">Dapatkan software dan lisensi original untuk mendukung kebutuhan perangkat Anda dengan mudah dan terpercaya!</p>
                    </div>
                </div><!--end grid-->

                <div class="relative animate-[spin_30s_linear_infinite] -z-1">
                    <span class="after:absolute after:start-0 after:bottom-1/2 after:translate-y-1/2 after:h-2 after:w-8 after:rounded-md after:bg-violet-600/20 relative after:z-10"></span>
                    <span class="after:absolute after:start-0 after:bottom-1/2 after:translate-y-1/2 after:rotate-90 after:h-2 after:w-8 after:rounded-md after:bg-violet-600/20 relative after:z-10"></span>
                </div>
            </div>
      

      <!-- Filter Tabs -->
      <div class="grid grid-cols-1 items-center gap-[30px] mt-10 mb-10">
        <div class="filters-group-wrap text-center">
          <div class="filters-group">
            <ul class="mb-0 list-none container-filter-box filter-options">
              <li
                class="inline-block font-medium text-base mx-1.5 mb-3 py-1 px-3 cursor-pointer relative text-slate-400 border border-gray-100 dark:border-gray-700 rounded-full transition duration-500"
                :class="selectedCategory == null ? 'active' : ''"
                @click="$router.push('/explore-workshop')"
              >
                <i class="uil uil-browser"></i> Workshop
              </li>
              <li
                class="inline-block font-medium text-base mx-1.5 mb-3 py-1 px-3 cursor-pointer relative border border-gray-100 dark:border-gray-700 rounded-full transition duration-500"
                :class="selectedCategory == 'teknisi' ? 'bg-violet-600 text-white border-violet-600' : 'text-slate-400'"
                @click="$router.push('/explore-teknisi')"
              >
                <i class="uil uil-volleyball" :class="selectedCategory == 'teknisi' ? 'text-white' : ''"></i> Teknisi
              </li>
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

        <section class="relative">
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
import searchbar from '@/components/searchbarBelanja.vue';
import items from '@/components/discover-lisensi.vue';
import pagination from '@/components/pagination.vue';
import switcher from '@/components/switcher.vue';
import footers from '@/components/footer/footer.vue'

</script>

<style lang="scss" scoped>

</style>