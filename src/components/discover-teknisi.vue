<template>
  <div class="font-inter">
    <div class="max-w-7xl mx-auto px-6 py-16 grid grid-cols-1 lg:grid-cols-4 gap-10">
      <!-- 🔹 Sidebar Filter -->
        <!-- 🔹 Sidebar Filter -->
      <aside
        class="modern-filter-card p-6 rounded-3xl shadow-[0_4px_20px_rgba(0,0,0,0.05)] bg-white border border-gray-100"
      >
        <!-- Header -->
        <div class="mb-6">
          <div class="flex items-center gap-3 mb-1">
            <h3 class="text-xl font-semibold text-gray-900 font-geist">Filter Pencarian</h3>
          </div>
          <p class="text-gray-400 text-sm">Sesuaikan pencarian teknisi Anda</p>
        </div>

        <div class="space-y-5">
          <!-- Search -->
          <div class="filter-group">
            <div class="flex items-center gap-2 mb-1">
              <i class="mdi mdi-magnify text-gray-400"></i>
              <label>Search</label>
            </div>
            <input
              type="text"
              v-model="filters.keyword"
              class="filter-input"
              placeholder="Ketik nama atau layanan..."
            />
          </div>

          <!-- City -->
          <div class="filter-group">
            <div class="flex items-center gap-2 mb-1">
              <i class="mdi mdi-city-variant-outline text-gray-400"></i>
              <label>Kota</label>
            </div>
            <select v-model="filters.city" class="filter-input">
              <option value="">Semua Kota</option>
              <option v-for="city in cities" :key="city" :value="city">{{ city }}</option>
            </select>
          </div>

          <!-- Status -->
          <div class="filter-group">
            <div class="flex items-center gap-2 mb-1">
              <i class="mdi mdi-power text-gray-400"></i>
              <label>Status</label>
            </div>
            <div class="flex flex-col gap-2 pl-1">
              <label class="flex items-center gap-2 text-gray-600 text-sm">
                <input type="checkbox" value="online" v-model="filters.status" class="checkbox-modern" />
                Online
              </label>
              <label class="flex items-center gap-2 text-gray-600 text-sm">
                <input type="checkbox" value="offline" v-model="filters.status" class="checkbox-modern" />
                Offline
              </label>
            </div>
          </div>

          <!-- Services -->
          <div class="filter-group">
            <div class="flex items-center gap-2 mb-1">
              <i class="mdi mdi-cog-outline text-gray-400"></i>
              <label>Layanan</label>
            </div>
            <div class="flex flex-col gap-2 pl-1">
              <label
                v-for="service in allServices"
                :key="service"
                class="flex items-center gap-2 text-gray-600 text-sm"
              >
                <input type="checkbox" :value="service" v-model="filters.services" class="checkbox-modern" />
                {{ service }}
              </label>
            </div>
          </div>
        </div>

        <!-- Divider -->
        <div class="h-px bg-gray-100 my-6"></div>

        <!-- Buttons -->
        <div class="space-y-3">
          <button
            @click="applyFilters"
            class="w-full py-3 bg-emerald-500 text-white rounded-2xl font-semibold font-geist hover:bg-gray-800 transition-all shadow-md hover:shadow-lg flex items-center justify-center gap-2"
          >
            <i class="mdi mdi-tune-variant text-md"></i>
            Apply Filter
          </button>

          <button
            @click="resetFilters"
            class="w-full py-3 bg-gray-100 text-gray-700 rounded-2xl font-medium font-geist hover:bg-gray-200 transition-all"
          >
            Reset
          </button>
        </div>
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
               <div class="flex items-center gap-3 mb-2">
                <div class="badge-tag">
                  <!-- <span class="text-[#F1592A]">//</span> -->
                  <span class="mx-1 text-black font-geist font-bold text-lg">{{ product.display_name }}</span>
                  <!-- <span class="text-[#F1592A]">//</span> -->
                </div>
              </div>

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
            <div class="flex justify-between items-center mt-auto">
             <div class="price-badge">
  <i class="mdi mdi-fire text-emerald-700 text-lg"></i>
  <span class="font-semibold text-emerald-700">{{ product.price }}</span>
</div>

          <router-link
            :to="{ name: 'details-technician', params: { id: product.id } }"
            class="explore-btn"
          >
            <span class="btn-text">Detail</span>
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
    },
    applyFilters() {
      // Optional: tampilkan notifikasi kecil atau animasi loading
      console.log('Filter applied:', this.filters)
    }
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Geist:wght@400;500;600;700;800&display=swap');
.font-geist {
  font-family: 'Geist', sans-serif;
}

/* === Filter Styling === */
.filter-card {
  position: relative;
  background: white;
  overflow: hidden;
}

.filter-card::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(16, 185, 129, 0.05), rgba(241, 89, 42, 0.05));
  z-index: 0;
}

.filter-card > * {
  position: relative;
  z-index: 1;
}

.filter-group {
  margin-bottom: 1.25rem;
}

.filter-group label {
  display: block;
  font-size: 0.85rem;
  font-weight: 600;
  color: #065f46;
  margin-bottom: 0.4rem;
  font-family: 'Geist', sans-serif;
}

.filter-input {
  width: 100%;
  padding: 0.6rem 0.75rem;
  border: 1.5px solid #e5e7eb;
  border-radius: 0.75rem;
  background-color: #fafafa;
  font-size: 0.875rem;
  transition: all 0.2s ease;
}

.filter-input:focus {
  border-color: #10b981;
  background-color: white;
  outline: none;
  box-shadow: 0 0 0 3px rgba(16, 185, 129, 0.15);
}

.filter-checkbox input {
  accent-color: #10b981;
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

.badge-tag {
  display: inline-flex;
  align-items: center;
  background-color: #efefef; /* hitam pekat */
  padding: 6px 16px;
  border-radius: 9999px; /* bentuk oval */
  font-weight: 600;
  font-family: 'Geist', sans-serif;
  font-size: 1rem; /* kira-kira text-sm */
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.25);
  letter-spacing: 0.3px;
  user-select: none;
  transition: all 0.3s ease;
}

.badge-tag:hover {
  transform: translateY(-1px);
  background-color: #1a1a1a;
}

/* Tambahkan style modern filter dari Untitled-1 */
.modern-filter-card {
  transition: all 0.3s ease;
}
.modern-filter-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.08);
}
.filter-group label {
  font-weight: 600;
  color: #374151;
  font-size: 0.85rem;
}
.filter-input {
  width: 100%;
  padding: 0.65rem 0.9rem;
  border: 1.5px solid #e5e7eb;
  border-radius: 1rem;
  background-color: #fafafa;
  font-size: 0.875rem;
  transition: all 0.2s ease;
}
.filter-input:focus {
  border-color: #111;
  background-color: #fff;
  outline: none;
  box-shadow: 0 0 0 4px rgba(0, 0, 0, 0.05);
}
.checkbox-modern {
  width: 16px;
  height: 16px;
  border-radius: 4px;
  border: 1.5px solid #d1d5db;
  accent-color: #111;
}
</style>
