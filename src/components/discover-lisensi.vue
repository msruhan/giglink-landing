<template>
  <div>
    <!-- MOBILE VIEW (2 kolom) -->
    <div class="grid grid-cols-2 gap-3 px-3 mt-6 sm:hidden">
      <div
        v-for="license in setlicenseData.slice(0, itemsToShow)"
        :key="license.id"
        class="group"
      >
        <div class="relative flex flex-col rounded-2xl bg-white shadow-sm border border-gray-100 overflow-hidden hover:shadow-md transition-all duration-300">
          <!-- ...existing code for mobile card... -->
          <div class="relative bg-gray-50 rounded-t-2xl overflow-hidden">
            <img :src="license.image_url_1" alt="license image" class="w-full h-32 object-cover transition-transform duration-500 group-hover:scale-105" />
            <span v-if="license.type === 'New'" class="absolute top-2 left-2 bg-gray-800 text-white text-[10px] font-medium px-2 py-0.5 rounded-full">New</span>
          </div>
          <router-link :to="{ name: 'details-license', params: { id: license.id } }" class="flex flex-col justify-between flex-1 bg-gray-50 px-2.5 py-3 text-left">
            <h3 class="text-[13px] font-semibold text-gray-900 leading-snug line-clamp-2 mb-1">{{ license.title }}</h3>
            <div class="flex items-center gap-1 mb-1">
              <img src="/src/assets/images/avatar/3.jpg" class="h-4 w-4 rounded-full object-cover" alt="Foto Penjual" />
              <span class="text-[11px] text-slate-800 font-medium truncate">{{ license.penjual || 'Penjual' }}</span>
            </div>
            <div class="flex flex-wrap items-center gap-1 text-[11px] text-slate-400 mb-2">
              <i class="mdi mdi-eye text-[13px]"></i> {{ license.views || 0 }}
              <span class="flex items-center"><i class="mdi mdi-star text-yellow-400 text-[13px]"></i>{{ license.rating || 0 }}/5</span>
              <span v-if="license.license_type" :class="['inline-block px-1 py-0 rounded-full text-[10px] font-semibold border', license.license_type === 'license' ? 'bg-emerald-500 text-white border-emerald-300' : license.license_type === 'credit' ? 'bg-yellow-100 text-yellow-700 border-yellow-300' : 'bg-gray-100 text-gray-700 border-gray-300']">{{ license.license_type }}</span>
            </div>
            <div class="flex items-center justify-between gap-1">
              <button class="flex items-center justify-center h-8 w-8 bg-white rounded-md border border-gray-200 text-gray-600 hover:shadow transition"><i class="mdi mdi-message-text-outline text-[16px]"></i></button>
              <div class="flex-1 text-center font-bold text-[13px] bg-white border border-gray-200 rounded-md h-8 flex items-center justify-center text-gray-900">{{ formatRupiah(license.price) }}</div>
              <button class="flex items-center justify-center h-8 w-8 bg-white rounded-md border border-gray-200 text-gray-600 hover:shadow transition"><i class="mdi mdi-cart-outline text-[16px]"></i></button>
            </div>
            <span v-if="license.posting" class="text-[10px] text-slate-400 italic mt-1 block">{{ license.posting }}</span>
          </router-link>
        </div>
      </div>
    </div>

    <!-- DESKTOP VIEW (responsive grid & card style like marketplace) -->
       <!-- Grid Produk -->
    <div class="grid xl:grid-cols-4 lg:grid-cols-3 md:grid-cols-2 sm:grid-cols-2 grid-cols-2 mt-10 gap-[30px]">
      <div
        v-for="license in setlicenseData.slice(0, 4)"
        :key="license.id"
        class="group flex flex-col items-center"
      >
        <!-- CARD UTAMA -->
        <div class="relative w-full rounded-2xl bg-white p-2 flex flex-col justify-between overflow-hidden">
          <!-- CARD ATAS (gambar produk) -->
          <div
            class="relative z-10 bg-gray-50 rounded-2xl overflow-hidden shadow-md"
          >
            <img
              :src="license.image_url_1"
              class="w-full h-48 object-cover rounded-2xl transition-transform duration-500 group-hover:scale-105"
              alt="license image"
            />
          </div>

          <!-- CARD BAWAH (judul, harga, fitur) -->
          <router-link
            :to="{name: 'item-detail', params: {id: license.id}}"
            class="relative w-full rounded-2xl bg-gray-50 mt-4 text-left px-4 pb-6 pt-8 -mt-6 shadow-inner block group overflow-hidden"
          >
            <h3 class="text-md font-semibold text-gray-900 font-inter mb-3 mt-2">
              {{ license.title }}
            </h3>

            <!-- Info Penjual -->
            <div class="flex items-center space-x-3 mb-1">
              <div class="relative">
                <img :src="avatarDefault" class="h-5 w-5 rounded-full object-cover" alt="Foto Penjual">
                <i class="mdi mdi-check-decagram text-emerald-600 text-md absolute -top-2 -end-2"></i>
              </div>
              <div class="flex items-center gap-2">
                <span class="font-semibold text-xs text-slate-900 dark:text-white">{{ license?.penjual || 'Penjual' }}</span>
              </div>
            </div>

            <!-- Info Rating & Kondisi -->
            <div class="flex flex-wrap items-center gap-2 text-xs text-slate-400 mb-3">
              <i class="mdi mdi-eye"></i> {{ license.views || 0 }}x dilihat
              <span class="flex items-center">
                <i class="mdi mdi-star text-yellow-400"></i> {{ license.rating || 0 }}/5
              </span>
              <span
                v-if="license.kondisi"
                :class="[ 'inline-block px-2 py-0.5 rounded-full text-xs font-semibold border',
                  license.kondisi === 'Baru' ? 'bg-emerald-500 text-white border-emerald-300' :
                  license.kondisi === 'Bekas' ? 'bg-yellow-100 text-yellow-700 border-yellow-300' :
                  'bg-gray-100 text-gray-700 border-gray-300' ]"
              >
                {{ license.kondisi }}
              </span>
            </div>

            <!-- BARIS BAWAH (Chat - Harga - Cart) -->
            <div class="mt-2 text-gray-900 flex items-center justify-start w-full gap-2 mr-2">
              <!-- Tombol Chat -->
              <button
                class="flex items-center justify-center h-10 w-10 bg-white rounded-md shadow-sm border border-gray-200 text-sm font-semibold text-gray-900 transition hover:shadow-md shrink-0"
              >
                <i class="mdi mdi-message-text-outline text-lg text-gray-500"></i>
              </button>

              <!-- Harga -->
              <div
                class="flex items-center justify-center flex-1 h-10 bg-white rounded-md shadow-sm border border-gray-200 text-sm font-bold text-gray-900 transition hover:shadow-md text-center"
              >
                {{ formatRupiah(license.price) }}
              </div>

              <!-- Tombol Cart -->
              <button
                class="flex items-center justify-center h-10 w-10 bg-white rounded-md shadow-sm border border-gray-200 text-sm font-semibold text-gray-900 transition hover:shadow-md shrink-0"
              >
                <i class="mdi mdi-cart-outline text-lg text-gray-500"></i>
              </button>
            </div>

            <span v-if="license.posting" class="text-xs text-slate-400 italic block mt-2">{{ license.posting }}</span>
          </router-link>

          <!-- BADGE OPTIONAL -->
          <span
            v-if="license.type === 'New'"
            class="absolute top-2 left-2 bg-gray-800 text-white text-xs font-medium px-3 py-1 rounded-full z-20"
          >
            New
          </span>
        </div>
      </div>
    </div>

    <div class="w-full" style="height: 120px;"></div>
  </div>
</template>

<script>
import { useLicenseStore } from '@/stores/storeLicense'
export default {
  props: ['discover', 'items', 'moreitem', 'explore'],
  name: 'ExploreOne',
  data() {
    return {
      setlicenseData: [],
      itemsToShow: 8,
    }
  },
  mounted() {
    const licenseStore = useLicenseStore()
    licenseStore.getLicenses().then(() => {
      this.setlicenseData = licenseStore.licenses.map(item => ({
        ...item,
        remaining: this.tickTock(item.date),
      }))
      this.setPostingInfo()
    })
    this._interval = setInterval(() => {
      const licenseStore = useLicenseStore()
      this.setlicenseData = licenseStore.licenses.map(item => ({
        ...item,
        remaining: this.tickTock(item.date),
      }))
      this.setPostingInfo()
    }, 1000)

    window.addEventListener('scroll', this.handleScroll)
  },
  beforeUnmount() {
    clearInterval(this._interval)
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll() {
      const scrollY = window.scrollY || window.pageYOffset
      const windowHeight = window.innerHeight
      const docHeight = document.documentElement.scrollHeight
      if (scrollY + windowHeight >= docHeight - 100 && this.itemsToShow < this.setlicenseData.length) {
        this.itemsToShow += 8
      }
    },
    tickTock(date) {
      let startDate = new Date(date)
      let currentDate = new Date()
      const diff = startDate.getTime() - currentDate.getTime()
      const days = Math.floor(diff / (1000 * 60 * 60 * 24))
      const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
      const minutes = Math.floor((diff / (1000 * 60)) % 60)
      const seconds = Math.floor((diff / 1000) % 60)
      return { days, hours, minutes, seconds }
    },
    setPostingInfo() {
      const now = new Date()
      this.setlicenseData = this.setlicenseData.map(item => {
        if (!item.postingDate) return item
        const postingDate = new Date(item.postingDate)
        const diffTime = now - postingDate
        const diffDays = Math.floor(diffTime / (1000 * 60 * 60 * 24))
        let posting = ''
        if (diffDays === 0) posting = 'Iklan diposting hari ini'
        else if (diffDays === 1) posting = 'Iklan diposting 1 hari yang lalu'
        else posting = `Iklan diposting ${diffDays} hari yang lalu`
        return { ...item, posting }
      })
    },
    formatRupiah(value) {
      if (!value) return 'Rp0'
      return 'Rp' + value.toString().replace(/\B(?=(\d{3})+(?!\d))/g, '.')
    },
  },
}
</script>
