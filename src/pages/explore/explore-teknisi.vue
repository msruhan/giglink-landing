<template>
  <div class="bg-[#f4f4f4] text-[#1a1a1a] min-h-screen">
    <navbar :navLight="'nav-dark'" :logoLight="true" />

    <!-- Start Hero -->
    <section class="relative md:pt-48 pt-36 overflow-hidden">
      <div class="container hidden sm:block">
        <div class="grid grid-cols-1 justify-center text-center mt-10">
          <div class="relative">
            <div class="relative mb-5">
              <h1
                class="text-5xl md:text-6xl font-extrabold tracking-tight text-gray-900 mb-6 leading-tight font-inter"
              >
                <span class="text-gray-900">Temukan Teknisi Profesional untuk Kebutuhan</span> <span class="text-emerald-500">Remote / Service Online.</span>
              </h1>
            </div>
            <p class="text-[#555] text-lg max-w-xl mx-auto font-inter">Tanya jawab dan konsultasi seputar permasalahan perangkat Anda secara online dengan mudah dan cepat!</p>
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
                class="inline-block font-medium text-base mx-1.5 mb-3 py-2 px-4 cursor-pointer relative rounded-full transition duration-500 font-inter"
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

    <!-- <div class="relative">
      <div
        class="shape absolute start-0 end-0 sm:-bottom-px -bottom-[2px] overflow-hidden z-1 text-white dark:text-slate-900"
      >
        <svg class="w-full h-auto" viewBox="0 0 2880 48" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path
            d="M0 48H1437.5H2880V0H2160C1442.5 52 720 0 720 0H0V48Z"
            fill="currentColor"
          ></path>
        </svg>
      </div>
    </div> -->

    <!-- Start List Teknisi -->
    <section>
      <div class="container">
        <searchbar :searchbar2="true" />
      </div>
    </section>

    <discover-workshop :teknisi-list="teknisiList" @open-detail="openDetail" />
    <switcher />
    <!-- <footers /> -->
  </div>
</template>

<script setup>
import { ref } from "vue";
import navbar from "@/components/navbar/navbar.vue";
import pagination from "@/components/pagination.vue";
import switcher from "@/components/switcher.vue";
import footers from "@/components/footer/footer.vue";
import searchbar from "@/components/nft-searchbar.vue";
import discoverWorkshop from "@/components/discover-workshop.vue";

const selectedCategory = ref("teknisi");
const selectedTech = ref(null);

const openDetail = (tech) => {
  selectedTech.value = tech;
};
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
