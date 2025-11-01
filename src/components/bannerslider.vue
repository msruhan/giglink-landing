<template>
  <div class="relative w-full overflow-hidden rounded-2xl">
    <!-- Slides -->
    <div
      class="flex transition-transform duration-700 ease-in-out"
      :style="{ transform: `translateX(-${currentIndex * 100}%)` }"
    >
      <div
        v-for="(banner, index) in banners"
        :key="index"
        class="w-full flex-shrink-0 px-2"
      >
        <div
          class="relative bg-white rounded-2xl p-6 flex items-center justify-between overflow-hidden"
          :style="{ backgroundColor: banner.bgColor }"
        >
          <div class="z-10">
            <h3 class="text-lg font-semibold text-gray-900 mb-2 leading-tight">
              {{ banner.title }}
            </h3>
            <p class="text-sm text-gray-700 mb-3">{{ banner.subtitle }}</p>
            <button
              class="bg-gray-900 text-white text-sm font-medium px-4 py-2 rounded-xl hover:bg-gray-800 transition"
            >
              {{ banner.buttonText }}
            </button>
          </div>
          <img
            :src="banner.image"
            alt="banner"
            class="w-24 h-24 object-cover rounded-xl z-0"
          />
        </div>
      </div>
    </div>

    <!-- Pagination Dots -->
    <div class="absolute bottom-3 left-1/2 -translate-x-1/2 flex space-x-2">
      <button
        v-for="(banner, index) in banners"
        :key="index"
        @click="goToSlide(index)"
        class="w-2.5 h-2.5 rounded-full transition-all duration-300"
        :class="index === currentIndex ? 'bg-emerald-500 w-5' : 'bg-gray-300'"
      ></button>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const banners = ref([
  {
    title: 'Get your special sale up to 50%',
    subtitle: 'Limited time offer only this week!',
    buttonText: 'Shop now',
    image: 'https://via.placeholder.com/150x150.png?text=Promo+1',
    bgColor: '#F3E8FF',
  },
  {
    title: 'Discount 20% for accessories!',
    subtitle: 'Grab your headphones now!',
    buttonText: 'Shop now',
    image: 'https://via.placeholder.com/150x150.png?text=Promo+2',
    bgColor: '#E0F7F0',
  },
  {
    title: 'Upgrade your device easily!',
    subtitle: 'Find best deals on gadgets',
    buttonText: 'Shop now',
    image: 'https://via.placeholder.com/150x150.png?text=Promo+3',
    bgColor: '#FFF4E5',
  },
])

const currentIndex = ref(0)
let autoSlide

const goToSlide = (index) => {
  currentIndex.value = index
}

const nextSlide = () => {
  currentIndex.value = (currentIndex.value + 1) % banners.value.length
}


function shuffle(array) {
  for (let i = array.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [array[i], array[j]] = [array[j], array[i]];
  }
  return array;
}

onMounted(() => {
  // Shuffle banners for randomness
  banners.value = shuffle(banners.value)
  // Start with a random banner
  currentIndex.value = Math.floor(Math.random() * banners.value.length)
  autoSlide = setInterval(nextSlide, 4000)
})

onBeforeUnmount(() => {
  clearInterval(autoSlide)
})
</script>

<style scoped>
/* Smooth slide transition */
.flex {
  transition: transform 0.7s ease-in-out;
}
</style>
