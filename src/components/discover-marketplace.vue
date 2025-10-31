<template>
  <div>
    <!-- Grid Produk -->
    <div class="grid xl:grid-cols-4 lg:grid-cols-3 md:grid-cols-2 sm:grid-cols-2 grid-cols-2 mt-10 gap-[30px]">
      <div
        v-for="product in setProductData.slice(0, 4)"
        :key="product.id"
        class="group flex flex-col items-center"
      >
        <!-- CARD UTAMA -->
        <div class="relative w-full rounded-2xl bg-white p-2 flex flex-col justify-between overflow-hidden">
          <!-- CARD ATAS (gambar produk) -->
          <div
            class="relative z-10 bg-gray-50 rounded-2xl overflow-hidden shadow-md"
          >
            <img
              :src="product.image_url_1"
              class="w-full h-48 object-cover rounded-2xl transition-transform duration-500 group-hover:scale-105"
              alt="product image"
            />
          </div>

          <!-- CARD BAWAH (judul, harga, fitur) -->
          <router-link
            :to="{name: 'item-detail', params: {id: product.id}}"
            class="relative w-full rounded-2xl bg-gray-50 mt-4 text-left px-4 pb-6 pt-8 -mt-6 shadow-inner block group overflow-hidden"
          >
            <h3 class="text-md font-semibold text-gray-900 font-inter mb-3 mt-2">
              {{ product.title }}
            </h3>

            <!-- Info Penjual -->
            <div class="flex items-center space-x-3 mb-1">
              <div class="relative">
                <img :src="avatarDefault" class="h-5 w-5 rounded-full object-cover" alt="Foto Penjual">
                <i class="mdi mdi-check-decagram text-emerald-600 text-md absolute -top-2 -end-2"></i>
              </div>
              <div class="flex items-center gap-2">
                <span class="font-semibold text-xs text-slate-900 dark:text-white">{{ product?.penjual || 'Penjual' }}</span>
              </div>
            </div>

            <!-- Info Rating & Kondisi -->
            <div class="flex flex-wrap items-center gap-2 text-xs text-slate-400 mb-3">
              <i class="mdi mdi-eye"></i> {{ product.views || 0 }}x dilihat
              <span class="flex items-center">
                <i class="mdi mdi-star text-yellow-400"></i> {{ product.rating || 0 }}/5
              </span>
              <span
                v-if="product.kondisi"
                :class="[ 'inline-block px-2 py-0.5 rounded-full text-xs font-semibold border',
                  product.kondisi === 'Baru' ? 'bg-emerald-500 text-white border-emerald-300' :
                  product.kondisi === 'Bekas' ? 'bg-yellow-100 text-yellow-700 border-yellow-300' :
                  'bg-gray-100 text-gray-700 border-gray-300' ]"
              >
                {{ product.kondisi }}
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
                {{ formatRupiah(product.price) }}
              </div>

              <!-- Tombol Cart -->
              <button
                class="flex items-center justify-center h-10 w-10 bg-white rounded-md shadow-sm border border-gray-200 text-sm font-semibold text-gray-900 transition hover:shadow-md shrink-0"
              >
                <i class="mdi mdi-cart-outline text-lg text-gray-500"></i>
              </button>
            </div>

            <span v-if="product.posting" class="text-xs text-slate-400 italic block mt-2">{{ product.posting }}</span>
          </router-link>

          <!-- BADGE OPTIONAL -->
          <span
            v-if="product.type === 'New'"
            class="absolute top-2 left-2 bg-gray-800 text-white text-xs font-medium px-3 py-1 rounded-full z-20"
          >
            New
          </span>
        </div>
      </div>
    </div>
  </div>
</template>



<script>
import { useProductStore } from '@/stores/storeProduct'
import avatarDefault from '@/assets/images/avatar/3.jpg'


export default {
  name: 'ProductCard',
  data() {
    return {
      setProductData: [],
      avatarDefault: avatarDefault,
    }
  },
  mounted() {
    const productStore = useProductStore()
    productStore.getProducts().then(() => {
      this.setProductData = productStore.products
    })
  },
  methods: {
    formatRupiah(value) {
      if (!value) return 'Rp0';
      // Hilangkan dua digit 0 di belakang koma jika ada
      let strValue = value.toString();
      if (strValue.includes('.')) {
        strValue = strValue.replace(/\.00$/, '');
      }
      return (
        'Rp' + strValue.replace(/\B(?=(\d{3})+(?!\d))/g, '.')
      );
    },
  },
}
</script>

<style scoped>
.group:hover img {
  transform: scale(1.05);
}
</style>
