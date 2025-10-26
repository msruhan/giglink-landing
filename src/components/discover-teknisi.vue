<template>
  <div>
    <!-- Main Section -->
    <div class="max-w-7xl mx-auto px-6 py-16 grid grid-cols-1 lg:grid-cols-4 gap-10">
      

      <!-- Filter Sidebar: Desktop -->
      <aside class="bg-white dark:bg-slate-900 shadow-xl rounded-2xl p-6 h-fit border border-gray-200 dark:border-slate-700 hidden sm:block">
        <h3 class="text-lg font-semibold text-slate-800 dark:text-white mb-4">Filter Pencarian</h3>
        <div class="mb-5">
          <label class="text-sm text-slate-600 dark:text-slate-300 mb-1 block">Search your keyword</label>
          <input type="text" v-model="filters.keyword" class="w-full p-2 border rounded-lg dark:bg-slate-800 dark:text-white" placeholder="Search your keyword..." />
        </div>
        <div class="mb-5">
          <label class="text-sm text-slate-600 dark:text-slate-300 mb-1 block">Kota</label>
          <select v-model="filters.city" class="w-full p-2 border rounded-lg dark:bg-slate-800 dark:text-white">
            <option value="">Semua Kota</option>
            <option v-for="city in cities" :key="city" :value="city">{{ city }}</option>
          </select>
        </div>
        <div class="mb-5">
          <label class="text-sm text-slate-600 dark:text-slate-300 mb-1 block">Status</label>
          <div class="flex flex-col gap-2">
            <label><input type="checkbox" value="online" v-model="filters.status" /> Online</label>
            <label><input type="checkbox" value="offline" v-model="filters.status" /> Offline</label>
          </div>
        </div>
        <div class="mb-5">
          <label class="text-sm text-slate-600 dark:text-slate-300 mb-1 block">Layanan</label>
          <div class="flex flex-col gap-2">
            <label v-for="service in allServices" :key="service">
              <input type="checkbox" :value="service" v-model="filters.services" /> {{ service }}
            </label>
          </div>
        </div>
        <button @click="resetFilters" class="w-full mt-4 py-2 bg-violet-600 text-white rounded-lg hover:bg-violet-700 transition">Reset Filter</button>
      </aside>

      <!-- Filter Button: Mobile -->
      <div class="sm:hidden mb-4">
        <button @click="showMobileFilter = true" class="w-full py-2 bg-violet-600 text-white rounded-lg font-semibold">Filter Pencarian</button>
        <div v-if="showMobileFilter" class="fixed inset-0 z-50 bg-black bg-opacity-40 flex items-center justify-center">
          <div class="bg-white dark:bg-slate-900 rounded-2xl p-6 w-11/12 max-w-sm mx-auto border border-gray-200 dark:border-slate-700">
            <h3 class="text-lg font-semibold text-slate-800 dark:text-white mb-4">Filter Pencarian</h3>
            <div class="mb-4">
              <label class="text-sm text-slate-600 dark:text-slate-300 mb-1 block">Search your keyword</label>
              <input type="text" v-model="filters.keyword" class="w-full p-2 border rounded-lg dark:bg-slate-800 dark:text-white" placeholder="Search your keyword..." />
            </div>
            <div class="mb-4">
              <label class="text-sm text-slate-600 dark:text-slate-300 mb-1 block">Kota</label>
              <select v-model="filters.city" class="w-full p-2 border rounded-lg dark:bg-slate-800 dark:text-white">
                <option value="">Semua Kota</option>
                <option v-for="city in cities" :key="city" :value="city">{{ city }}</option>
              </select>
            </div>
            <div class="mb-4">
              <label class="text-sm text-slate-600 dark:text-slate-300 mb-1 block">Status</label>
              <div class="flex gap-4">
                <label><input type="checkbox" value="online" v-model="filters.status" /> Online</label>
                <label><input type="checkbox" value="offline" v-model="filters.status" /> Offline</label>
              </div>
            </div>
            <div class="mb-4">
              <label class="text-sm text-slate-600 dark:text-slate-300 mb-1 block">Layanan</label>
              <div class="flex flex-wrap gap-2">
                <label v-for="service in allServices" :key="service">
                  <input type="checkbox" :value="service" v-model="filters.services" /> {{ service }}
                </label>
              </div>
            </div>
            <div class="flex gap-2 mt-4">
              <button @click="resetFilters" class="flex-1 py-2 bg-violet-600 text-white rounded-lg hover:bg-violet-700 transition">Reset</button>
              <button @click="showMobileFilter = false" class="flex-1 py-2 bg-gray-200 dark:bg-slate-700 text-slate-800 dark:text-white rounded-lg">Tutup</button>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Technician List -->
      <div class="lg:col-span-3 space-y-8">
        <div
          v-if="filteredProducts.length === 0"
          class="text-center text-gray-500 py-20"
        >
          <p class="text-lg font-medium">
            Tidak ada workshop yang cocok dengan filter Anda.
          </p>
        </div>

        <div
          v-for="product in filteredProducts"
          :key="product.id"
          class="bg-white dark:bg-slate-900 border border-gray-100 dark:border-slate-700 shadow-lg rounded-2xl p-5 sm:p-8 lg:p-12 hover:shadow-2xl transition-all duration-300 flex flex-col sm:flex-row justify-between items-start sm:items-center min-h-[120px] sm:min-h-[160px] gap-4 sm:gap-0"
        >
          <div class="flex items-center gap-4">
            <img
              :src="product.image_url"
              class="w-16 h-16 sm:w-24 sm:h-24 lg:w-28 lg:h-28 rounded-xl border-4 shadow-lg object-cover flex-shrink-0"
            />
            <div>
              <h4 class="text-lg sm:text-xl lg:text-2xl font-bold text-slate-800 dark:text-white">
                {{ product.display_name }}
              </h4>
              <div class="text-sm sm:text-base text-slate-500 flex items-center gap-1 mt-1">
                <i class="mdi mdi-map-marker"></i> {{ product.location }}
              </div>
              <div class="flex flex-wrap gap-1 sm:gap-2 mt-2 sm:mt-3">
                <span
                  v-for="service in product.services"
                  :key="service"
                  class="text-xs sm:text-sm bg-violet-100 text-violet-700 px-2 sm:px-3 py-0.5 sm:py-1 rounded-full font-semibold"
                >
                  {{ service }}
                </span>
              </div>
              <div class="mt-2 sm:mt-3 text-sm sm:text-base text-slate-600 dark:text-slate-300">
                {{ product.short_description }}
              </div>
            </div>
          </div>

          <div class="mt-4 sm:mt-0 text-right">
            <div class="flex flex-col items-end sm:items-end text-right w-full sm:w-auto">
              <p class="text-base sm:text-xl font-bold text-violet-600 dark:text-white w-full sm:w-auto">
                {{ product.price }}
              </p>
              <p class="text-sm sm:text-base text-slate-500 dark:text-slate-400 mt-1 w-full sm:w-auto">
                {{ product.duration }}
              </p>
              <router-link
                :to="{ name: 'details-technician', params: { id: product.id } }"
                class="inline-block mt-3 sm:mt-4 w-full sm:w-auto px-4 sm:px-5 py-2 sm:py-3 rounded-lg bg-violet-600 text-sm sm:text-lg text-white hover:bg-violet-700 transition font-bold text-center"
              >
                Informasi Detail
              </router-link>
            </div>
          </div>
        </div>
      </div>


      


    </div>
  </div>
</template>

<script>
import { useTechnicianStore } from '@/stores/storeTechnician'

export default {
  name: "WorkshopList",
  data() {
    return {
      setProductData: [],
      filters: {
        city: '',
        status: [],
        services: [],
        keyword: ''
      },
      showMobileFilter: false,
      cities: ['Jakarta', 'Bandung', 'Surabaya', 'Yogyakarta', 'Bali'],
      allServices: ['Servis HP', 'Ganti LCD', 'Software', 'Unlock', 'Cleaning', 'Sparepart'],
      datas: [
        {
          id: 41,
          mainimage: require('../assets/images/items/1.gif'),
          type: 'Listing',
          time: '3min 50sec ago',
          title: "QUEEN'S COURT - Silver Card #72/250 was put up for sale for"
        },
        {
          id: 1,
          mainimage: require('../assets/images/items/1.jpg'),
          type: 'Sale',
          time: '3min 50sec ago',
          title: 'ethkun #5001 was sold for $9.27.'
        },
        {
          id: 3,
          mainimage: require('../assets/images/items/2.jpg'),
          type: 'Offer',
          time: '3min 50sec ago',
          title: 'A global offer of $100.00 was placed for FACES'
        },
        {
          id: 4,
          mainimage: require('../assets/images/items/3.jpg'),
          type: 'Deposit',
          time: '3min 50sec ago',
          title: 'Anatomy Science Ape Club #1113 was sold for $32.87.'
        },
        {
          id: 2,
          mainimage: require('../assets/images/items/2.gif'),
          type: 'Listing',
          time: '3min 50sec ago',
          title: 'Swiss Army Man #16/30 was sold for $600.00.'
        },
        {
          id: 6,
          mainimage: require('../assets/images/items/4.jpg'),
          type: 'Sale',
          time: '3min 50sec ago',
          title: 'Unsupervised — Machine Hallucinations — MoMA Dreams — I by Refik Anadol #84/100, 1 AP was sold for $1,210.16.'
        },
        {
          id: 5,
          mainimage: require('../assets/images/items/3.gif'),
          type: 'Listing',
          time: '3min 50sec ago',
          title: '3D Bear #7333 was put up for sale for $8.00.'
        },
      ],
      types: [
        {
          icon: 'uil uil-wallet me-1',
          name: 'Purchased'
        },
        {
          icon: 'uil uil-tag-alt me-1',
          name: 'Sales'
        },
        {
          icon: 'uil uil-fire me-1',
          name: 'Burns'
        },
        {
          icon: 'uil uil-heart me-1',
          name: 'Likes'
        },
        {
          icon: 'uil uil-browser me-1',
          name: 'Bids'
        },
        {
          icon: 'uil uil-users-alt me-1',
          name: 'Following'
        },
        {
          icon: 'uil uil-list-ui-alt me-1',
          name: 'Listing'
        },
        {
          icon: 'uil uil-music me-1',
          name: 'Music'
        },
        {
          icon: 'uil uil-camera me-1',
          name: 'Video'
        },
        {
          icon: 'uil uil-illustration me-1',
          name: 'Illustration'
        },
      ]
    }
  },
  computed: {
    filteredProducts() {
      return this.setProductData.filter(p => {
        const byCity = !this.filters.city || p.location === this.filters.city
        const byStatus =
          this.filters.status.length === 0 ||
          this.filters.status.includes(p.online ? 'online' : 'offline')
        const byService =
          this.filters.services.length === 0 ||
          p.services.some(s => this.filters.services.includes(s))
        return byCity && byStatus && byService
      })
    }
  },
  mounted() {
    const technicianStore = useTechnicianStore()
    technicianStore.getTechnicians().then(() => {
      this.setProductData = technicianStore.technicians.map(item => ({
        ...item,
        online: Math.random() > 0.5, // demo status online/offline
        services: item.services || ['Servis HP', 'Software'],
        price: item.price || 'Rp 150.000 - Rp 500.000',
        duration: 'Waktu pengerjaan 1-3 hari',
        location: item.location || 'Jakarta',
      }))
    })
  },
  methods: {
    resetFilters() {
      this.filters = { city: '', status: [], services: [] }
    }
  }
}


</script>

<style scoped>
/* Tidak perlu membatasi max-width container lagi */
</style>
