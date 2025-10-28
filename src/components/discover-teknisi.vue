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
      <div class="lg:col-span-3 space-y-2">
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
            <div class="flex items-center justify-between mb-1">
              <div class="flex items-center gap-3">
                <h3 class="text-lg font-bold text-gray-900 dark:text-white font-geist tracking-tight">
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

            <p class="text-sm font-bold text-gray-500 dark:text-slate-300 mb-3 font-inter">
              {{ product.short_description }}
            </p>

            <div class="flex flex-wrap gap-2 mb-3">
              <span
                v-for="srv in product.services"
                :key="srv"
                class="inline-flex items-center gap-1 bg-[#f4f4f4] dark:bg-slate-800 text-[#1a1a1a] dark:text-white px-2 py-0.5 rounded-xl text-xs font-inter font-semibold border border-gray-200 dark:border-slate-600 font"
              >
                <i class="mdi mdi-tools text-gray-500 text-base"></i>
                {{ srv }}
              </span>
              
            </div>
<!-- 
               'Servis HP': 'mdi-cellphone-cog',
        'Ganti LCD': 'mdi-cellphone-link',
        'Software': 'mdi-android',
        'Unlock': 'mdi-lock-open-outline',
        'Cleaning': 'mdi-water',
        'Sparepart': 'mdi-tools', -->

            <div class="flex justify-between items-center mt-auto">
              <p class="text-emerald-600 dark:text-emerald-400 font-semibold text-sm sm:text-base">
                {{ product.price }}
              </p>
          <router-link
            :to="{ name: 'details-technician', params: { id: product.id } }"
            class="explore-btn"
          >
            <span class="btn-text">Informasi Detail</span>
            <span class="btn-icon">
              <i class="mdi mdi-magnify"></i>
            </span>
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

.explore-btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: #111; /* hitam pekat */
  color: white;
  padding: 10px 20px;
  border-radius: 9999px; /* membuat oval */
  font-weight: 600;
  font-size: 0.875rem;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.25);
  transition: all 0.3s ease;
}

.explore-btn:hover {
  background: #1a1a1a;
  transform: translateY(-1px);
  box-shadow: 0 6px 14px rgba(0, 0, 0, 0.3);
}

.btn-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #10b981; /* warna hijau emerald */
  color: white;
  border-radius: 50%;
  width: 26px;
  height: 26px;
  font-size: 1.1rem;
}

.btn-text {
  font-family: 'Geist', sans-serif;
}


</style>
