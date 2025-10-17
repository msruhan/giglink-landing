<template>
  <div class="container mx-auto py-8">
    <div class="flex flex-col lg:flex-row gap-8">
      <!-- Main Content -->
      <div class="flex-1 space-y-8">
        <!-- Profile Card -->
        <div class="bg-gradient-to-r from-violet-600 to-blue-400 rounded-2xl shadow-lg p-8 flex flex-col md:flex-row gap-8 items-center relative overflow-hidden">
          <img :src="imageSrc2" class="w-40 h-40 object-cover border-4 border-white shadow-xl rounded-2xl bg-white" alt="Profile" />
          <div class="flex-1 text-center md:text-left text-white">
            <h2 class="text-3xl font-extrabold flex items-center justify-center md:justify-start gap-2">
              {{ workshop?.name || '-' }}
              <i class="mdi mdi-check-decagram text-emerald-300 text-2xl"></i>
            </h2>
            <p class="text-blue-100 text-lg mt-1">UI UX Designer & Workshop Owner</p>
            <div class="flex flex-wrap justify-center md:justify-start gap-4 mt-2 text-blue-200 text-sm">
              {{ workshop?.location || '-' }}
              <span class="flex items-center gap-1"><i class="mdi mdi-map-marker"></i> {{ workshop?.location || '-' }}</span>
              <span class="flex items-center gap-1"><i class="mdi mdi-calendar"></i> {{ workshop?.date || '-' }}</span>
              <span class="flex items-center gap-1"><i class="mdi mdi-star"></i> {{ workshop?.rating || '-' }}, {{ workshop?.reviews || '-' }}</span>
            </div>
            <div class="flex flex-wrap gap-2 mt-4 justify-center md:justify-start">
              <button class="btn btn-sm rounded-full bg-white text-violet-700 hover:bg-violet-100 font-bold"><i class="mdi mdi-plus"></i> Follow</button>
              <a href="#" class="btn btn-icon btn-sm rounded-full bg-red-600 hover:bg-red-700 text-white" title="Youtube"><i class="mdi mdi-youtube"></i></a>
              <a href="#" class="btn btn-icon btn-sm rounded-full bg-gradient-to-tr from-purple-600 to-yellow-400 hover:from-pink-600 hover:to-yellow-600 text-white" title="Instagram"><i class="mdi mdi-instagram"></i></a>
              <a href="#" class="btn btn-icon btn-sm rounded-full bg-blue-600 hover:bg-blue-800 text-white" title="Facebook"><i class="mdi mdi-facebook"></i></a>
              <a href="#" class="btn btn-icon btn-sm rounded-full bg-green-500 hover:bg-green-700 text-white" title="WhatsApp"><i class="mdi mdi-whatsapp"></i></a>
            </div>
          </div>
        </div>

        <!-- About/Description -->
        <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6">
          <h3 class="text-2xl font-bold mb-3 text-violet-700">Tentang Toko</h3>
          <p class="text-slate-600 dark:text-slate-300 mb-2">{{ workshop?.description || '-' }}</p>
          <ul class="flex flex-wrap gap-4 mt-4 text-sm text-slate-500">
            <li><span class="font-semibold text-violet-600">Layanan:</span> {{ workshop?.info || '-' }}</li>
            <li><span class="font-semibold text-violet-600">Spesialisasi:</span> {{ workshop?.specialization || '-' }}</li>
            <li><span class="font-semibold text-violet-600">Jam Operasional:</span> {{ workshop?.operation_hours || '-' }}</li>
          </ul>
        </div>

        <!-- Stats -->
        <div class="flex flex-col gap-6 mt-8">
          <div class="bg-violet-50 dark:bg-slate-800 rounded-2xl p-6 flex flex-row items-center gap-6">
            <span class="mdi mdi-thumb-up text-4xl text-violet-600"></span>
            <div>
              <span class="font-extrabold text-lg block">{{ workshop?.total_devices_fixed || '-' }}</span>
              <span class="text-sm text-slate-400 block">Device telah diperbaiki</span>
            </div>
          </div>
          <div class="bg-violet-50 dark:bg-slate-800 rounded-2xl p-6 flex flex-row items-center gap-6">
            <span class="mdi mdi-briefcase-check text-4xl text-violet-600"></span>
            <div>
              <span class="font-extrabold text-lg block">Teknisi Profesional</span>
              <span class="text-sm text-slate-400 block">Teknisi Bersertifikat & Peralatan Modern</span>
            </div>
          </div>
          <div class="bg-violet-50 dark:bg-slate-800 rounded-2xl p-6 flex flex-row items-center gap-6">
            <span class="mdi mdi-progress-clock text-4xl text-violet-600"></span>
            <div>
              <span class="font-extrabold text-lg block">Gratis Antar & Jemput</span>
              <span class="text-sm text-slate-400 block">Antar Jemput Gratis</span>
            </div>
          </div>
          <div class="bg-violet-50 dark:bg-slate-800 rounded-2xl p-6 flex flex-row items-center gap-6">
            <span class="mdi mdi-account-heart text-4xl text-violet-600"></span>
            <div>
              <span class="font-extrabold text-lg block">Cepat & Aman</span>
              <span class="text-sm text-slate-400 block">Perbaikan Cepat & Bisa Ditunggu</span>
            </div>
          </div>
        </div>

        <!-- Portfolio Gallery Slider -->
        <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6">
          <h3 class="text-2xl font-bold mb-3 text-violet-700">Portofolio</h3>
          <div class="relative w-full max-w-xl mx-auto">
            <img :src="portfolioImages[portfolioIndex]" class="w-full h-64 object-cover rounded-lg shadow" alt="Portfolio" />
            <button @click="prevPortfolio" class="absolute left-2 top-1/2 -translate-y-1/2 bg-violet-600 text-white rounded-full p-2 shadow hover:bg-violet-700"><i class="mdi mdi-chevron-left text-2xl"></i></button>
            <button @click="nextPortfolio" class="absolute right-2 top-1/2 -translate-y-1/2 bg-violet-600 text-white rounded-full p-2 shadow hover:bg-violet-700"><i class="mdi mdi-chevron-right text-2xl"></i></button>
            <div class="flex justify-center gap-2 mt-3">
              <span v-for="(img, idx) in portfolioImages" :key="idx" :class="['w-3 h-3 rounded-full', idx === portfolioIndex ? 'bg-violet-600' : 'bg-gray-300']"></span>
            </div>
          </div>
        </div>

        <!-- Reviews -->
        <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6">
          <h3 class="text-2xl font-bold mb-3 text-violet-700">Review Pelanggan</h3>
          <div class="space-y-6">
            <div v-for="i in 2" :key="i" class="flex gap-4 items-start bg-violet-50 dark:bg-slate-800 rounded-lg p-4">
              <img :src="imageSrc2" class="w-12 h-12 rounded-full object-cover border-2 border-violet-400" alt="Reviewer" />
              <div class="flex-1">
                <div class="flex flex-wrap justify-between items-center">
                  <div>
                    <h4 class="font-semibold text-violet-700">Theresa Phillips</h4>
                    <div class="flex gap-4 text-xs text-slate-400 mt-1">
                      <span><i class="mdi mdi-star"></i> 5.0 (346 Reviews)</span>
                      <span><i class="mdi mdi-calendar"></i> 1 min ago</span>
                    </div>
                  </div>
                  <div class="text-right">
                    <div class="font-bold text-lg text-violet-600">$40-$500</div>
                    <span class="text-xs text-slate-400">Price : Fixed</span>
                  </div>
                </div>
                <p class="text-slate-500 mt-2">Pelayanan sangat memuaskan, teknisi ramah dan profesional. Proses cepat dan hasil memuaskan. Sangat direkomendasikan!</p>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Sidebar -->
      <div class="w-full lg:w-80 flex-shrink-0 space-y-6">
        <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6">
          <h4 class="font-bold text-lg mb-2 text-violet-700">Info Kontak</h4>
          <div class="text-2xl font-bold text-violet-600 mb-1">$125 - $180</div>
          <div class="text-slate-400 text-sm mb-4">Hourly Rate</div>
          <ul class="space-y-2 text-sm">
            <li class="flex items-center gap-2"><i class="mdi mdi-map-marker"></i> <span>{{ workshop?.location || '-' }}</span></li>
            <li class="flex items-center gap-2"><i class="mdi mdi-briefcase"></i> <span>5 Years Experience</span></li>
            <li class="flex items-center gap-2"><i class="mdi mdi-calendar"></i> <span>Delivery: 3-5 Days</span></li>
            <li class="flex items-center gap-2"><i class="mdi mdi-web"></i> <span>Language: Basic</span></li>
            <li class="flex items-center gap-2"><i class="mdi mdi-phone"></i> <span>{{ workshop?.whatsapp || '-' }}</span></li>
            <li class="flex items-center gap-2"><i class="mdi mdi-email"></i> <span>{{ workshop?.email || '-' }}</span></li>
          </ul>
          <router-link :to="{name: 'creator-chat'}" class="btn btn-primary w-full mt-4"> Hubungi</router-link>
        </div>
        <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6">
          <h4 class="font-bold text-lg mb-2 text-violet-700">Keahlian</h4>
          <div v-if="workshop?.specialization && workshop?.specialization.length" class="flex flex-wrap items-center gap-2 mt-2">
              <span
                v-for="(specialization, idx) in (Array.isArray(workshop.specialization) ? workshop.specialization : workshop.specialization.split(','))"
                :key="idx"
                class="px-2 py-0.5 rounded-full bg-violet-100 text-violet-700 text-xs font-medium border border-violet-200"
               >
                {{ specialization.trim() }}
              </span>
          </div>
        </div>
        <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6">
          <h4 class="font-bold text-lg mb-2 text-violet-700">Lokasi Toko</h4>
          <div class="aspect-video rounded-lg overflow-hidden">
            <iframe src="https://www.google.com/maps/embed?pb=!1m16!1m12!1m3!1d2965.0824050173574!2d-93.63905729999999!3d41.998507000000004!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!2m1!1sWebFilings%2C+University+Boulevard%2C+Ames%2C+IA!5e0!3m2!1sen!2sus!4v1390839289319" width="100%" height="200" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import images2 from '../assets/images/avatar/1.jpg'
import { ref, onMounted, watch } from 'vue'
import { useWorkshopStore } from '@/stores/storeWorkshop'

const props = defineProps({ id: [String, Number] })
const workshopStore = useWorkshopStore()
const workshop = ref(null)
const imageSrc2 = ref(images2)
const portfolioImages = ref([
  imageSrc2.value,
  imageSrc2.value,
  imageSrc2.value,
  imageSrc2.value,
  imageSrc2.value,
  imageSrc2.value
])
const portfolioIndex = ref(0)

const fetchWorkshop = async () => {
  workshop.value = await workshopStore.getDetailWorkshops(props.id)
}

onMounted(fetchWorkshop)
watch(() => props.id, fetchWorkshop)

function prevPortfolio() {
  portfolioIndex.value = (portfolioIndex.value - 1 + portfolioImages.value.length) % portfolioImages.value.length
}
function nextPortfolio() {
  portfolioIndex.value = (portfolioIndex.value + 1) % portfolioImages.value.length
}
</script>

<style lang="scss" scoped>
.btn {
  @apply px-4 py-2 rounded-full font-semibold shadow transition;
}
.btn-primary {
  @apply bg-violet-600 hover:bg-violet-700 text-white;
}
</style>