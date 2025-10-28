<template>
  <div class="font-inter">
    <div class="max-w-7xl mx-auto px-6 py-16 grid grid-cols-1 lg:grid-cols-4 gap-10">
      <!-- 🔹 Sidebar Filter -->
      <aside
        class="bg-white dark:bg-slate-900 shadow-xl rounded-2xl p-6 h-fit border border-gray-200 dark:border-slate-700 hidden sm:block"
      >
        <h3 class="text-lg font-semibold text-emerald-500 mb-4">Filter Pencarian</h3>
        <div class="mb-5">
          <label class="text-sm text-slate-600 dark:text-slate-300 mb-1 block"
            >Search your keyword</label
          >
          <input
            type="text"
            v-model="filters.keyword"
            class="w-full p-2 border rounded-lg dark:bg-slate-800 dark:text-white font-inter"
            placeholder="Search your keyword..."
          />
        </div>
        <div class="mb-5">
          <label class="text-sm text-slate-600 dark:text-slate-300 mb-1 block">Kota</label>
          <select
            v-model="filters.city"
            class="w-full p-2 border rounded-lg dark:bg-slate-800 dark:text-white font-inter"
          >
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
        <button
          @click="resetFilters"
          class="w-full mt-4 py-2 bg-emerald-500 text-white rounded-lg hover:bg-emerald-600 transition font-inter"
        >
          Reset Filter
        </button>
      </aside>

      <!-- 🔹 Daftar Workshop -->
      <div class="lg:col-span-3 space-y-8">
        <div
          v-if="filteredProducts.length === 0"
          class="text-center text-gray-500 py-20 font-inter"
        >
          <p class="text-lg font-medium">Tidak ada workshop yang cocok dengan filter Anda.</p>
        </div>

        <div
          v-for="(product, index) in filteredProducts"
          :key="product.id"
          class="relative bg-white dark:bg-slate-900 rounded-2xl shadow-md p-6 border border-gray-100 dark:border-slate-700 hover:shadow-xl transition-all duration-300 flex flex-col sm:flex-row items-start gap-6"
        >
          <!-- Garis penghubung antar card -->
          <div
            v-if="index !== filteredProducts.length - 1"
            class="absolute left-8 top-20 w-px bg-gray-200 dark:bg-slate-700 hidden lg:block"
          ></div>

          <!-- 🔸 Gambar -->
          <div class="flex-shrink-0">
            <img
              :src="product.image_url"
              alt="foto teknisi"
              class="w-24 h-24 sm:w-28 sm:h-28 rounded-xl object-cover border-4 border-gray-200 shadow-md"
            />
          </div>

          <!-- 🔸 Konten Utama -->
          <div class="flex-1">
            <div class="flex items-center justify-between mb-3">
              <div class="flex items-center gap-3">
                <div
                  class="w-8 h-8 flex items-center justify-center rounded-full border-2 border-gray-800 dark:border-white"
                >
                  <i class="mdi mdi-wrench text-lg text-gray-800 dark:text-white"></i>
                </div>
                <h3 class="text-lg font-semibold text-gray-900 dark:text-white font-geist">
                  {{ product.display_name }}
                </h3>
              </div>
              <div class="flex gap-1">
                <span
                  v-for="dot in 3"
                  :key="dot"
                  class="w-2 h-2 rounded-full"
                  :class="dot <= index + 1 ? 'bg-emerald-500' : 'bg-gray-200 dark:bg-slate-700'"
                ></span>
              </div>
            </div>

            <p class="text-sm text-gray-600 dark:text-slate-300 mb-3">
              {{ product.short_description }}
            </p>

            <div class="flex flex-wrap gap-2 mb-3">
              <span
                v-for="srv in product.services"
                :key="srv"
                class="inline-flex items-center gap-1 bg-[#f4f4f4] dark:bg-slate-800 text-[#1a1a1a] dark:text-white px-3 py-1 rounded-xl text-xs font-medium border border-gray-200 dark:border-slate-600"
              >
                <i class="mdi mdi-wrench text-[#F1592A] text-base"></i>
                {{ srv }}
              </span>
            </div>

            <div class="flex justify-between items-center mt-auto">
              <p class="text-emerald-600 dark:text-emerald-400 font-semibold text-sm sm:text-base">
                {{ product.price }}
              </p>
              <router-link
                :to="{ name: 'details-technician', params: { id: product.id } }"
                class="px-4 py-1.5 rounded-full bg-emerald-500 text-white hover:bg-emerald-600 text-sm font-semibold shadow"
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
  name: 'WorkshopListWithSidebar',
  data() {
    return {
      setProductData: [],
      filters: {
        city: '',
        status: [],
        services: [],
        keyword: ''
      },
      cities: ['Jakarta', 'Bandung', 'Surabaya', 'Yogyakarta', 'Bali'],
      allServices: ['Servis HP', 'Ganti LCD', 'Software', 'Unlock', 'Cleaning', 'Sparepart']
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
        const byKeyword =
          !this.filters.keyword ||
          p.display_name.toLowerCase().includes(this.filters.keyword.toLowerCase())
        return byCity && byStatus && byService && byKeyword
      })
    }
  },
  mounted() {
    const technicianStore = useTechnicianStore()
    technicianStore.getTechnicians().then(() => {
      this.setProductData = technicianStore.technicians.map((item, i) => ({
        ...item,
        display_name: item.display_name || ['Subscribe', 'Request', 'Approve or Revise'][i] || 'Workshop',
        short_description:
          item.short_description ||
          [
            'Pick a plan that fits your workflow',
            'Submit tasks via your design portal',
            'Receive designs in 2–3 business days'
          ][i] ||
          'Deskripsi singkat workshop.',
        image_url: item.image_url || `https://randomuser.me/api/portraits/men/${30 + i}.jpg`,
        price: item.price || 'Rp 150.000 - Rp 500.000',
        location: item.location || 'Jakarta',
        services: item.services || ['Servis HP', 'Software', 'Unlock'],
        online: Math.random() > 0.5
      }))
    })
  },
  methods: {
    resetFilters() {
      this.filters = { city: '', status: [], services: [], keyword: '' }
    }
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Geist:wght@400;500;600;700;800&display=swap');
.font-geist {
  font-family: 'Geist', sans-serif;
}
</style>
