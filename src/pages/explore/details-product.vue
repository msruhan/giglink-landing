<template>
  <div>
    <navbar />
    <section class="relative pt-28 md:pb-24 pb-16">
      <div class="container">
        <div class="grid lg:grid-cols-12 md:grid-cols-2 grid-cols-1 gap-[30px]">
          <!-- Main Image and Thumbnails -->
        <div class="lg:col-span-6">

        <!-- Galeri Produk -->
        <div class="lg:col-span-6 flex flex-col items-center">
          <!-- Gambar Utama (lebih besar & sejajar dengan card penjual) -->
          <div class="relative w-full flex justify-center items-center mb-4">
              <button
              @click="prevImage"
              class="absolute left-3 bg-white/80 hover:bg-white text-gray-600 rounded-full p-2 shadow-md transition"
              >
              <i class="mdi mdi-chevron-left text-2xl"></i>
              </button>

              <img
              :src="selectedImage"
              alt="Foto Produk Utama"
              class="rounded-xl shadow-lg object-contain w-full max-h-[520px] transition-all"
              />

              <button
              @click="nextImage"
              class="absolute right-3 bg-white/80 hover:bg-white text-gray-600 rounded-full p-2 shadow-md transition"
              >
              <i class="mdi mdi-chevron-right text-2xl"></i>
              </button>
          </div>

          <!-- Thumbnails di bawah gambar utama -->
          <div class="flex justify-center flex-wrap gap-3 w-full hidden sm:flex">
              <div
              v-for="(img, idx) in productImages"
              :key="idx"
              @click="selectedImage = img"
              :class="[ 
                  'cursor-pointer border rounded-md overflow-hidden transition-all',
                  selectedImage === img
                  ? 'border-blue-500 ring-2 ring-blue-400 scale-105'
                  : 'border-gray-200 hover:border-blue-400'
              ]"
              >
              <img
                  :src="img"
                  class="object-cover w-24 h-24 md:w-28 md:h-28"
                  alt="Thumbnail"
              />
              </div>
          </div>
        </div>

            <!-- Card Penjual -->
            <div class="flex items-center justify-between bg-gray-50 dark:bg-slate-800 rounded-lg shadow dark:shadow-gray-700 p-4 mt-6 mb-6">
                <!-- Info Penjual -->
                <div class="flex items-center space-x-3">
                    <div class="relative">
                    <img :src="avatarDefault" class="h-12 w-12 rounded-full object-cover" alt="Foto Penjual">
                    <i class="mdi mdi-check-decagram text-emerald-600 text-lg absolute -top-2 -end-2"></i>
                    </div>

                    <div>
                    <div class="flex items-center gap-2">
                        <span class="font-semibold text-slate-900 dark:text-white">{{ product?.penjual || 'Penjual' }}</span>
                    </div>
                    <span class="text-slate-400 text-sm">Penjual</span>
                    </div>
                </div>

                <!-- Tombol Chat -->
                <button
                  v-if="product?.whatsapp"
                  @click="chatWhatsapp"
                  class="flex items-center gap-2 bg-green-600 hover:bg-green-700 text-white font-medium rounded-full px-4 py-2 transition"
                >
                  <i class="mdi mdi-whatsapp text-white text-lg"></i>
                  Whatsapp
                </button>
            </div>
                

            <!-- Bagikan ke Sosial Media -->
            <div class="mt-8 border-t pt-6 hidden sm:flex">
                <div class="flex flex-col sm:flex-row sm:items-center sm:justify-between gap-4">
                    <!-- Bagikan -->
                    <div>
                    <div class="flex items-center gap-2 mb-3">
                        <i class="mdi mdi-share-outline text-xl text-gray-700"></i>
                        <span class="font-medium text-gray-800 dark:text-white">Bagikan</span>
                    </div>

                    <div class="flex items-center gap-4 text-gray-600">
                        <a href="#" class="hover:text-blue-500 transition"><i class="mdi mdi-twitter text-2xl"></i></a>
                        <a href="#" class="hover:text-blue-700 transition"><i class="mdi mdi-facebook text-2xl"></i></a>
                        <a href="#" class="hover:text-pink-500 transition"><i class="mdi mdi-instagram text-2xl"></i></a>
                        <a href="#" class="hover:text-green-600 transition"><i class="mdi mdi-whatsapp text-2xl"></i></a>
                    </div>
                    </div>
                </div>
            </div>
        </div>


          <!-- Product Info -->
          <div class="lg:col-span-6 lg:ms-8">
            <div v-if="product?.kondisi" class="mb-1">
              <span
                v-if="product.kondisi === 'Baru'"
                class="inline-block px-3 py-1 text-xs font-bold rounded-full bg-blue-100 text-blue-700 uppercase"
              >{{ product.kondisi.toUpperCase() }}</span>
              <span
                v-else-if="product.kondisi === 'Bekas'"
                class="inline-block px-3 py-1 text-xs font-bold rounded-full bg-orange-100 text-orange-700 uppercase"
              >{{ product.kondisi.toUpperCase() }}</span>
            </div>
            <h1 class="md:text-3xl text-2xl font-bold mb-2">{{ product?.title || '' }}</h1>
            <div class="flex items-center gap-4 mb-4">
              <span class="text-blue-600 font-bold text-2xl">{{ formatRupiah(product?.price) }}</span>
            </div>
            <div class="flex gap-2 mb-4">
                <span class="flex items-center gap-1 px-3 py-1 rounded-full bg-gray-100 text-xs text-slate-600 font-medium">
                  <i class="mdi mdi-cart-outline text-base text-blue-500"></i>
                  Terjual {{ product?.sold || 0 }}x
                </span>
                <span class="flex items-center gap-1 px-3 py-1 rounded-full bg-gray-100 text-xs text-slate-600 font-medium">
                  <i class="mdi mdi-eye-outline text-base text-green-500"></i>
                  {{ product?.views || 0 }}x dilihat
                </span>
                <span class="flex items-center gap-1 px-3 py-1 rounded-full bg-yellow-100 text-xs text-yellow-700 font-medium">
                  <i class="mdi mdi-star text-base"></i>
                  {{ product?.rating || 0 }}/5
                </span>
              </div>
            <div>
              <div class="flex gap-2 mb-4">
                <button @click="activeTab = 'deskripsi'" :class="activeTab === 'deskripsi' ? 'bg-blue-900 text-white' : 'bg-gray-100 text-slate-600'" class="px-4 py-2 rounded-t-md font-semibold focus:outline-none">Deskripsi</button>
                <button @click="activeTab = 'spesifikasi'" :class="activeTab === 'spesifikasi' ? 'bg-blue-900 text-white' : 'bg-gray-100 text-slate-600'" class="px-4 py-2 rounded-t-md font-semibold focus:outline-none">Spesifikasi</button>
                <button @click="activeTab = 'info'" :class="activeTab === 'info' ? 'bg-blue-900 text-white' : 'bg-gray-100 text-slate-600'" class="px-4 py-2 rounded-t-md font-semibold focus:outline-none">Info Penting</button>
              </div>
              <div class="bg-gray-50 dark:bg-slate-800 rounded-b-md p-4 mb-6">
                <div v-if="activeTab === 'deskripsi'">
                  <ul class="list-disc pl-6 space-y-2 text-slate-500">
                    <li>
                      <span class="font-semibold text-slate-700 dark:text-white">Kondisi Barang:</span><br>
                      <span v-if="product?.description" class="dark:text-white" v-html="formatNewline(product?.description)"></span>
                    </li>
                    <li>
                      <span class="font-semibold text-slate-700 dark:text-white">Kelengkapan:</span><br>
                      <span v-if="product?.kelengkapan" class="dark:text-white" v-html="formatNewline(product?.kelengkapan)"></span>
                    </li>
                    <li>
                      <span class="font-semibold text-slate-700 dark:text-white">Kekurangan:</span><br>
                      <span v-if="product?.kekurangan" class="dark:text-white" v-html="formatNewline(product?.kekurangan)"></span>
                    </li>
                  </ul>
                </div>
                <div v-else-if="activeTab === 'spesifikasi'">
                  <div class="mb-3">
                    <table class="min-w-full bg-white dark:bg-slate-800 rounded-xl shadow border border-gray-200 dark:border-slate-700 overflow-hidden">
                      <tbody>
                        <tr class="even:bg-gray-50 even:dark:bg-slate-700">
                          <td class="px-6 py-3 font-semibold text-slate-700 dark:text-white w-40 border-b border-gray-100 dark:border-slate-700">Chipset</td>
                          <td class="px-6 py-3 text-black-700 dark:text-white-300 border-b border-gray-100 dark:border-slate-700">{{ product?.spesification.chipset || '' }}</td>
                        </tr>
                        <tr class="even:bg-gray-50 even:dark:bg-slate-700">
                          <td class="px-6 py-3 font-semibold text-slate-700 dark:text-white border-b border-gray-100 dark:border-slate-700">Layar</td>
                          <td class="px-6 py-3 text-black-700 dark:text-white-300 border-b border-gray-100 dark:border-slate-700">{{ product?.spesification.layar || '' }}</td>
                        </tr>
                        <tr class="even:bg-gray-50 even:dark:bg-slate-700">
                          <td class="px-6 py-3 font-semibold text-slate-700 dark:text-white border-b border-gray-100 dark:border-slate-700">Kamera</td>
                          <td class="px-6 py-3 text-black-700 dark:text-white-300 border-b border-gray-100 dark:border-slate-700">{{ product?.spesification.kamera || '' }}</td>
                        </tr>
                        <tr class="even:bg-gray-50 even:dark:bg-slate-700">
                          <td class="px-6 py-3 font-semibold text-slate-700 dark:text-white border-b border-gray-100 dark:border-slate-700">Baterai</td>
                          <td class="px-6 py-3 text-black-700 dark:text-white-300 border-b border-gray-100 dark:border-slate-700">{{ product?.spesification.baterai || '' }}</td>
                        </tr>
                        <tr class="even:bg-gray-50 even:dark:bg-slate-700">
                          <td class="px-6 py-3 font-semibold text-slate-700 dark:text-white">Warna</td>
                          <td class="px-6 py-3 text-black-700 dark:text-white-300 border-b border-gray-100 dark:border-slate-700">{{ product?.spesification.warna || '' }}</td>
                        </tr>
                      </tbody>
                    </table>
                  </div>
                </div>
                <div v-else>
                    <p class="text-slate-500 dark:text-white">{{ product?.info || 'Informasi belum tersedia.' }}</p>
                </div>
              </div>
            </div>

            <!-- Pilihan Model dan Kapasitas -->
            <div class="mb-6">
                <h2 class="font-semibold text-lg mb-3">Kapasitas</h2>
                <div class="grid grid-cols-2 sm:grid-cols-4 gap-3">
                    <button
                    v-for="(k, idx) in kapasitasList"
                    :key="'kapasitas-' + idx"
                    @click="enabledKapasitasList.includes(k) ? selectedKapasitas = k : null"
                    :disabled="!enabledKapasitasList.includes(k)"
                    :class="[
                      'border rounded-lg py-3 px-4 text-center font-medium transition',
                      selectedKapasitas === k
                        ? 'border-blue-500 ring-2 ring-blue-400 bg-blue-50 text-black dark:text-black'
                        : 'border-gray-300 hover:border-blue-400 text-slate-700',
                      !enabledKapasitasList.includes(k) ? 'opacity-50 cursor-not-allowed' : ''
                    ]"
                    >
                    {{ k }}
                    </button>
                </div>
            </div>

            <!-- Metode Pembayaran -->
            <div class="mb-10">
              <h2 class="font-semibold text-lg mb-3">Pilihan Pembayaran</h2>
              <div class="grid grid-cols-2 sm:grid-cols-4 gap-3">
                <button
                  v-for="(m, idx) in metodePembayaranList"
                  :key="'metode-' + idx"
                  @click="enabledMetodePembayaranList.includes(m) ? selectedMetodePembayaran = m : null"
                  :disabled="!enabledMetodePembayaranList.includes(m)"
                  :class="[
                    'border rounded-lg py-3 px-4 text-center font-medium transition flex items-center justify-center gap-2',
                    selectedMetodePembayaran === m
                      ? 'border-blue-500 ring-2 ring-blue-400 bg-blue-50 text-black dark:text-black'
                      : 'border-gray-300 hover:border-blue-400 text-slate-700',
                    !enabledMetodePembayaranList.includes(m) ? 'opacity-50 cursor-not-allowed' : ''
                  ]"
                >
                  <template v-if="m === 'Tokopedia'">
                    <img :src="tokopedia" alt="Tokopedia" class="w-6 h-6" />
                  </template>
                  <template v-else-if="m === 'Shopee'">
                    <img :src="shopee" alt="Shopee" class="w-6 h-6" />
                  </template>
                  <template v-else-if="m === 'Tiktok'">
                    <img :src="tiktok" alt="Tiktok" class="w-6 h-6" />
                  </template>
                  <template v-else>
                    <i class="mdi mdi-bank text-xl text-blue-700"></i>
                  </template>
                  <span>{{ m }}</span>
                </button>
              </div>
            </div>

            
            <div class="max-w-full w-full bg-white dark:bg-slate-800 rounded-lg shadow p-4 mt-6 mb-6 flex flex-col justify-between min-h-[180px]">
              <!-- Tombol aksi -->
              <div class="mt-2 space-y-3">
                <button
                  class="w-full rounded-lg py-4 bg-blue-900 text-white font-semibold text-lg hover:bg-blue-800 transition-shadow"
                  @click="handleBuyNow"
                >
                  Beli Langsung
                </button>
                <button
                  class="w-full rounded-lg py-4 border-2 border-blue-900 text-blue-900 font-semibold text-lg hover:bg-blue-50 flex items-center justify-center gap-2"
                  @click="handleAddToCart"
                >
                  <span class="text-2xl leading-none dark:text-blue">+</span>
                  <span class="dark:text-blue">Keranjang</span>
                </button>
              </div>
              <!-- Footer actions -->
              <div class="mt-6 border-t pt-4 text-sm text-gray-600 dark:text-gray-300">
                <div class="flex items-center justify-between gap-4">
                  <button class="flex items-center gap-2 hover:text-gray-800 dark:hover:text-white" @click="$emit('compare')">
                    <i class="mdi mdi-scale-balance text-lg"></i>
                    <span>Bandingkan</span>
                  </button>
                  <button class="flex items-center gap-2 hover:text-gray-800 dark:hover:text-white" @click="$emit('wishlist')">
                    <i class="mdi mdi-heart-outline text-lg"></i>
                    <span>Wishlist</span>
                  </button>
                  <button class="flex items-center gap-2 hover:text-gray-800 dark:hover:text-white" @click="$emit('share')">
                    <i class="mdi mdi-share-variant text-lg"></i>
                    <span>Share</span>
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div id="buynow" :class="isActive2 ? 'fixed' : 'hidden'" tabindex="-1"
        class="z-50 overflow-hidden inset-0 m-auto flex justify-center items-center">
        <div class="relative w-full h-auto max-w-md p-4">
            <div class="relative bg-white dark:bg-slate-900 rounded-lg shadow dark:shadow-gray-800">
                <div class="flex justify-between items-center px-6 py-4 border-b border-gray-100 dark:border-gray-700">
                    <h5 class="text-xl font-semibold">Checkout</h5>
                    <button type="button"
                        class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm p-1.5 ms-auto inline-flex items-center dark:hover:bg-gray-800 dark:hover:text-white"
                        data-modal-toggle="NftBuynow">
                        <svg @click="toggle2" class="size-5" fill="currentColor" viewBox="0 0 20 20"
                            xmlns="http://www.w3.org/2000/svg">
                            <path fill-rule="evenodd"
                                d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
                                clip-rule="evenodd"></path>
                        </svg>
                    </button>
                </div>
                <div class="p-6">
                  <form class="text-start">
                    <div class="grid grid-cols-1 gap-4">
                      <div>
                        <label class="font-semibold mb-2 block" for="model">Nama Barang</label>
                        <input
                          id="model"
                          type="text"
                          :value="selectedModel"
                          readonly
                          class="form-input w-full text-[15px] py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-blue-600 dark:border-gray-800 dark:focus:border-blue-600 focus:ring-0"
                        />
                      </div>
                      <div>
                        <label class="font-semibold mb-2 block" for="kapasitas">Kapasitas</label>
                        <input
                          id="kapasitas"
                          type="text"
                          :value="selectedKapasitas"
                          readonly
                          class="form-input w-full text-[15px] py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-blue-600 dark:border-gray-800 dark:focus:border-blue-600 focus:ring-0"
                        />
                      </div>
                      <div>
                        <label class="font-semibold mb-2 block" for="metode">Metode Pembayaran</label>
                        <div class="relative w-full">
                          <input
                            id="metode"
                            type="text"
                            readonly
                            class="form-input w-full text-[15px] py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-blue-600 dark:border-gray-800 dark:focus:border-blue-600 focus:ring-0 pr-32"
                          />
                          <span class="absolute left-3 top-1/2 -translate-y-1/2 px-4 py-1 text-xs font-bold rounded-full bg-orange-100 text-black-700 uppercase pointer-events-none dark:text-black">
                            {{ selectedMetodePembayaran }}
                          </span>
                        </div>
                      </div>
                      <div>
                        <label class="font-semibold mb-2 block" for="price">Total Harga</label>
                        <input
                          id="price"
                          type="text"
                          :value="formatRupiah(product?.price)"
                          readonly
                          class="form-input w-full text-[15px] py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-blue-600 dark:border-gray-800 dark:focus:border-blue-600 focus:ring-0 font-bold text-blue-600"
                        />
                      </div>
                    </div>
                  </form>

                  <div class="flex items-center p-4 bg-red-600/10 text-red-600 mt-4 rounded-lg">
                    <i class="uil uil-exclamation-octagon text-3xl"></i>
                    <div class="ms-2">
                      <span class="block font-semibold dark:text-white">Perhatian!</span>
                      <span class="block dark:text-white">Dengan melanjutkan pembayaran, kamu menyetujui S&amp;K yang berlaku</span>
                    </div>
                  </div>

                  <div class="mt-4">
                    <a href="javascript:void(0)" data-modal-toggle="NftBuynow"
                        class="btn rounded-full bg-blue-900 hover:bg-blue-700 border-blue-600 hover:border-blue-700 text-white w-full"><i
                            class="mdi mdi-lightning-bolt"></i> Bayar Sekarang</a>
                  </div>
                </div>
            </div>
        </div>
      </div>
    </section>
    <switcher />
    <!-- <footers /> -->
  </div>
</template>

<script setup>
import { ref, onMounted, computed } from 'vue'
import navbar from '@/components/navbar/navbar.vue';
import switcher from '@/components/switcher.vue';
import footers from '@/components/footer/footer.vue'
import { useRoute } from 'vue-router';
import image from '@/assets/images/items/3.gif'
import avatarDefault from '@/assets/images/avatar/3.jpg'
import { useProductStore } from '@/stores/storeProduct'
import tokopedia from '@/assets/images/tokopedia.png'
import shopee from '@/assets/images/shopee.png'
import tiktok from '@/assets/images/tiktok.png'

const route = useRoute();
const id = ref(route.params.id)
const product = ref(null)
const isActive2 = ref(false)
const activeTab = ref('deskripsi')
const productStore = useProductStore()

const models = ['iPhone 17 Pro', 'iPhone 17 Pro Max']
const kapasitasList = ['256 GB', '512 GB', '1 TB', '2 TB']

const enabledKapasitasList = computed(() => {
  let prodKapasitas = product.value?.kapasitas || product.value?.spesification?.kapasitas || ''
  let arr = []
  if (Array.isArray(prodKapasitas)) {
    arr = prodKapasitas
  } else if (typeof prodKapasitas === 'string') {
    arr = prodKapasitas.split(',').map(k => k.trim()).filter(Boolean)
  }
  return kapasitasList.filter(k => arr.includes(k))
})

const metodePembayaranList = ['Rekber', 'Tokopedia', 'Shopee', 'Tiktok']

const enabledMetodePembayaranList = computed(() => {
  const pembayaran = product.value?.pembayaran || {}
  return metodePembayaranList.filter(m => {
    if (m === 'Rekber') return pembayaran.rekber === 'YES'
    if (m === 'Tokopedia') return pembayaran.tokped === 'YES'
    if (m === 'Shopee') return pembayaran.shopee === 'YES'
    if (m === 'Tiktok') return pembayaran.tiktok === 'YES'
    return false
  })
})

const selectedModel = ref(models[1]) // default: iPhone 17 Pro Max
const selectedKapasitas = ref(kapasitasList[0]) // default: 256 GB
const selectedMetodePembayaran = ref(metodePembayaranList[0]) // default: Rekber

const productImages = ref([
  '/images/produk1.jpg',
  '/images/produk2.jpg',
  '/images/produk3.jpg',
  '/images/produk4.jpg'
])

const selectedImage = ref(productImages.value[0])
const yourPrice = ref("")

function prevImage() {
  let index = productImages.value.findIndex(img => img === selectedImage.value)
  if (index === -1) index = 0
  index = (index - 1 + productImages.value.length) % productImages.value.length
  selectedImage.value = productImages.value[index]
}

function nextImage() {
  let index = productImages.value.findIndex(img => img === selectedImage.value)
  if (index === -1) index = 0
  index = (index + 1) % productImages.value.length
  selectedImage.value = productImages.value[index]
}



function formatRupiah(value) {
  if (!value) return 'Rp0';
  return 'Rp' + value.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
}

function toggle2() {
  isActive2.value = !isActive2.value
}

function handleBuyNow() {
  isActive2.value = true
}

onMounted(async () => {
  if (id.value) {
    product.value = await productStore.getDetailProducts(id.value)
    // Parse spesification JSON string to object
    if (product.value && typeof product.value.spesification === 'string') {
      try {
        product.value.spesification = JSON.parse(product.value.spesification)
      } catch (e) {
        product.value.spesification = {}
      }
    }
    // Ambil gambar utama dan gambar tambahan dari variabel image_url_1, image_url_2, dst
    const images = []
    if (product.value.image_url_1) images.push(product.value.image_url_1)
    if (product.value.image_url_2) images.push(product.value.image_url_2)
    if (product.value.image_url_3) images.push(product.value.image_url_3)
    if (product.value.image_url_4) images.push(product.value.image_url_4)
    productImages.value = images.length ? images : ['/images/produk1.jpg']
    selectedImage.value = productImages.value[0]
    // Set default condition to 'new' if not present
    if (!product.value.condition) {
      product.value.condition = 'new'
    }
    // Set default selectedKapasitas ke kapasitas yang bisa dipilih
    if (enabledKapasitasList.value.length > 0) {
      selectedKapasitas.value = enabledKapasitasList.value[0]
    }
    // Set default selectedMetodePembayaran ke yang enabled
    if (enabledMetodePembayaranList.value.length > 0) {
      selectedMetodePembayaran.value = enabledMetodePembayaranList.value[0]
    }
  }
})

// Fungsi untuk mengubah newline (\n) menjadi <br>
function formatNewline(text) {
  if (!text) return '';
  return text.replace(/\n/g, '<br>');
}

// Fungsi untuk chat Whatsapp
function chatWhatsapp() {
  if (!product.value?.whatsapp) return;
  const phone = product.value.whatsapp.replace(/[^\d]/g, '');
  const seller = product.value.penjual || '';
  const title = product.value.title || '';
  const message = encodeURIComponent(`Halo ${seller} saya melihat iklan Anda di INDOTECHNICIANS. Apakah produk ${title} masih ada?`);
  const url = `https://wa.me/${phone}?text=${message}`;
  window.open(url, '_blank');
}
</script>

<style lang="scss" scoped></style>