<template>
  <section class="relative py-20 bg-white dark:bg-slate-900">
    <div class="container mx-auto px-6 text-center">
      <!-- 🌟 Badge -->
      <div class="flex justify-center mb-4">
        <span
          class="px-4 py-1 text-sm font-medium rounded-full border border-gray-300 bg-gray-50 text-gray-700"
        >
          Testimonials
        </span>
      </div>

      <!-- 🏷️ Judul -->
      <h2
        class="text-3xl md:text-4xl font-semibold text-gray-900 dark:text-white mb-2"
      >
        What our Clients Say
      </h2>
      <p class="text-gray-500 mb-10">
        Real feedback from companies we’ve helped grow.
      </p>

      <!-- 🌀 Swiper Slider -->
      <swiper
        :modules="[Autoplay, Pagination]"
        :slides-per-view="1"
        :space-between="30"
        :loop="true"
        :autoplay="{ delay: 4000, disableOnInteraction: false }"
        :breakpoints="{
          768: { slidesPerView: 2 },
          1024: { slidesPerView: 3 }
        }"
        class="pb-10"
      >
        <swiper-slide v-for="(testi, index) in testimonials" :key="index">
          <div
            class="bg-gray-50 dark:bg-slate-800 p-6 rounded-2xl shadow-sm text-left h-full flex flex-col justify-between"
          >
            <div class="font-inter">
              <p class="text-gray-700 dark:text-gray-300 mb-6 leading-relaxed">
                {{ testi.text }}
              </p>
            </div>
            <div class="flex items-center gap-3">
              <img
                :src="testi.image"
                alt="Avatar"
                class="w-10 h-10 rounded-full"
              />
              <div>
                <p class="font-semibold text-gray-900 dark:text-white">
                  {{ testi.name }}
                </p>
                <p class="text-sm text-gray-500">{{ testi.company }}</p>
              </div>
            </div>
          </div>
        </swiper-slide>

        <!-- Pagination bullets -->
        <div class="swiper-pagination !bottom-0"></div>
      </swiper>
    </div>
  </section>
</template>

<script setup>
import { Swiper, SwiperSlide } from "swiper/vue";
import { Autoplay, Pagination } from "swiper/modules";
import "swiper/css";
import "swiper/css/pagination";

const testimonials = [
  {
    name: "Adriana Novak",
    company: "Alpha Solutions",
    image: "https://randomuser.me/api/portraits/women/68.jpg",
    text: "Thanks to Spark, our customer engagement skyrocketed. Their innovative approach made a huge difference.",
  },
  {
    name: "John Smith",
    company: "Beta Solutions",
    image: "https://randomuser.me/api/portraits/men/44.jpg",
    text: "Spark’s blockchain solutions transformed our supply chain efficiency. Their expertise is truly unmatched.",
  },
  {
    name: "Robert Davis",
    company: "Gamma Solutions",
    image: "https://randomuser.me/api/portraits/men/32.jpg",
    text: "Thanks to Spark, our product development cycle was cut in half. Their support and expertise were invaluable.",
  },
  {
    name: "Clara Williams",
    company: "Delta Innovations",
    image: "https://randomuser.me/api/portraits/women/65.jpg",
    text: "We achieved better scalability and client satisfaction after implementing Spark’s tailored solutions.",
  },
];
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap');

.font-inter {
  font-family: 'Inter', sans-serif;
}

.swiper-pagination-bullet {
  background-color: #a1a1aa !important;
  opacity: 1;
}
.swiper-pagination-bullet-active {
  background-color: #7c3aed !important; /* violet tone */
}
</style>
