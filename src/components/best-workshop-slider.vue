<template>
  <div class="mt-12">
    <!-- <h3 class="md:text-[30px] text-[26px] font-semibold mb-4">Best Workshops</h3> -->
    <div class="relative">
      <div class="flex gap-6 overflow-x-auto pb-4 hide-scroll-bar">
        <div v-for="workshop in bestWorkshops" :key="workshop.id" class="min-w-[300px] bg-white dark:bg-slate-900 rounded-lg shadow p-6 flex flex-col items-center">
          <img :src="workshop.image_url_1 || require('@/assets/images/items/1.jpg')" class="w-60 h-60 object-cover rounded-md mb-3" alt="Workshop" />
           <router-link :to="{name: 'details-workshop', params: {id: workshop.id}}" class="text-lg font-semibold hover:text-violet-600">{{workshop.name}}</router-link>
          <div class="text-slate-600 dark:text-slate-200 text-center mb-2 line-clamp-2 min-h-[40px]">{{ workshop.short_description || '-' }}</div>
          <div class="flex items-center gap-2 text-xs text-slate-400">
            <i class="mdi mdi-star text-yellow-400"></i> {{ workshop.rating || 0 }}/5
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useWorkshopStore } from '@/stores/storeWorkshop'

const workshopStore = useWorkshopStore()
const bestWorkshops = ref([])

onMounted(async () => {
  await workshopStore.getWorkshop()
  // Sort by rating, take top 8
  bestWorkshops.value = [...workshopStore.workshops]
    .sort((a, b) => (b.rating || 0) - (a.rating || 0))
    .slice(0, 8)
})
</script>

<style scoped>
.hide-scroll-bar {
  -ms-overflow-style: none;
  scrollbar-width: none;
}
.hide-scroll-bar::-webkit-scrollbar {
  display: none;
}
</style>
