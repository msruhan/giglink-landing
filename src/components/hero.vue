<template>
  <section class="bg-gray-50 min-h-screen flex flex-col">
    <!-- Hero Content -->
    <div
      class="flex flex-col-reverse md:flex-row items-center justify-between flex-grow"
    >
      <!-- Left Text -->
      <div class="max-w-lg mx-auto text-center md:text-left space-y-6">
        <h1 class="text-5xl md:text-6xl font-extrabold leading-tight text-gray-900 font-inter">
          Secure <span class="text-emerald-500">business</span><br />
          with Techty <span class="text-gray-900">security.</span>
        </h1>

        <p class="text-gray-600 text-lg leading-relaxed">
          We have considered our solutions to support every stage of your growth.
          We are the fastest and easiest way to launch an attractive and
          feature-complete SaaS showcase.
        </p>
        

        <!-- CTA Buttons -->
        <div class="flex flex-wrap justify-center md:justify-start gap-4">
          <button
            class="bg-emerald-500 text-white px-6 py-3 rounded-lg font-semibold hover:bg-emerald-600 transition"
          >
            Request A Free Demo
          </button>
          <button
            class="border border-gray-300 px-6 py-3 rounded-lg font-semibold text-gray-700 hover:bg-gray-100 transition"
          >
            Hire An Expert
          </button>
        </div>
      </div>


      
      <!-- Right Image / Video -->
      <div class="relative w-full max-w-lg shadow-xl rounded-2xl overflow-hidden">
          <nftslider />

        <!-- Trustpilot -->
        <div
          class="absolute -bottom-14 left-0 right-0 mx-auto bg-white shadow-md rounded-xl px-5 py-3 flex items-center gap-4 w-fit"
          style="left:0;right:0;"
        >
          <div class="flex items-center gap-2">
            <span class="text-emerald-500 font-bold text-lg">★</span>
            <p class="font-semibold text-gray-800 font-inter">Trustpilot</p>
          </div>
          <div class="flex items-center gap-2 text-yellow-500">
            <span>★★★★★</span>
            <p class="text-gray-600 text-sm">4900+ 5 Stars</p>
          </div>
        </div>
      </div>
    </div>

    <!-- Logos Section -->
    <div class="mt-28 mb-16 text-center px-8">
      <p class="font-semibold text-gray-800 text-lg mb-6">
        Thousands of businesses use Techty.
      </p>

      <div class="flex flex-wrap justify-center gap-8 opacity-70">
        <img
          v-for="i in 5"
          :key="i"
          :src="`https://dummyimage.com/120x40/ccc/000&text=Logoipsum`"
          class="h-8"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
import nftslider from '@/components/nft-slider.vue'


</script>
<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap");
.font-inter {
  font-family: "Inter", sans-serif;
}
</style>
