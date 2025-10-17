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
            <div class="flex justify-center flex-wrap gap-3 w-full">
                <div
                v-for="(img, idx) in licenseImages"
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
                          <span class="font-semibold text-slate-900 dark:text-white">{{ license?.seller_name || 'Penjual' }}</span>
                      </div>
                      <span class="text-slate-400 text-sm">Penjual</span>
                      </div>
                  </div>

                  <!-- Tombol Chat -->
                  <router-link
                      :to="{ name: 'creator-chat', params: { id: license?.id } }"
                      class="flex items-center gap-2 bg-green-600 hover:bg-green-700 text-white font-medium rounded-full px-4 py-2 transition"
                  >
                      <i class="mdi mdi-chat text-white text-lg"></i>
                      Chat Penjual
                  </router-link>
              </div>

              <!-- Bagikan ke Sosial Media -->
              <div class="mt-8 border-t pt-6">
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


          <!-- license Info -->
          <div class="lg:col-span-6 lg:ms-8">
            <div v-if="license?.condition" class="mb-1">
              <span v-if="license.condition === 'new'" class="inline-block px-3 py-1 text-xs font-bold rounded-full bg-blue-100 text-blue-700">NEW</span>
              <span v-else-if="license.condition === 'second'" class="inline-block px-3 py-1 text-xs font-bold rounded-full bg-orange-100 text-orange-700">SECOND</span>
            </div>
            <h1 class="md:text-3xl text-2xl font-bold mb-2">{{ license?.name || '' }}</h1>
            <div class="flex items-center gap-3 mb-4">
              <span class="text-blue-600 font-semibold text-lg">{{ formatRupiah(license?.price) }}</span>
              <span class="text-xs text-slate-400">{{ license?.views || 0 }}x dilihat</span>
              <span class="flex items-center text-xs text-yellow-500"><i class="mdi mdi-star"></i> {{ license?.rating || 0 }}/5</span>
            </div>
            <div>
              <div class="flex gap-2 mb-4">
                <button @click="activeTab = 'deskripsi'" :class="activeTab === 'deskripsi' ? 'bg-blue-600 text-white' : 'bg-gray-100 text-slate-600'" class="px-4 py-2 rounded-t-md font-semibold focus:outline-none">Deskripsi</button>
                <button @click="activeTab = 'spesifikasi'" :class="activeTab === 'spesifikasi' ? 'bg-blue-600 text-white' : 'bg-gray-100 text-slate-600'" class="px-4 py-2 rounded-t-md font-semibold focus:outline-none">Spesifikasi</button>
                <button @click="activeTab = 'info'" :class="activeTab === 'info' ? 'bg-blue-600 text-white' : 'bg-gray-100 text-slate-600'" class="px-4 py-2 rounded-t-md font-semibold focus:outline-none">Info Penting</button>
              </div>
              <div class="bg-gray-50 dark:bg-slate-800 rounded-b-md p-4 mb-6">
                <div v-if="activeTab === 'deskripsi'">
                  <ul class="list-disc pl-6 space-y-2 text-slate-500">
                    <li>
                      <span class="font-semibold text-slate-700 dark:text-white">Deskripsi:</span><br>
                      <span v-if="license?.description" class="dark:text-white">{{ license?.description }}</span>
                    </li>
                  </ul>
                </div>
                <div v-else-if="activeTab === 'spesifikasi'">
                  <ul class="list-disc pl-6 space-y-2 text-slate-500">
                    <li>
                      <span class="font-semibold text-slate-700 dark:text-white">Spesifikasi:</span><br>
                      <span v-if="license?.spesification" class="dark:text-white">{{ license?.spesification }}</span>
                    </li>
                  </ul>
                </div>
                <div v-else>
                  <p class="text-slate-500 dark:text-white">{{ license?.info || 'Informasi belum tersedia.' }}</p>
                </div>
              </div>
            </div>
            <!-- Pilihan Model dan Kapasitas (dummy) -->
            <div class="mb-6">
              <h2 class="font-semibold text-lg mb-3">Jumlah</h2>
              <div class="relative flex items-center w-48">
                <button
                  type="button"
                  class="border rounded-l-lg py-2 px-3 text-center font-medium transition border-gray-300 hover:border-blue-400 text-slate-700 bg-gray-50 text-base"
                  @click="decrementModel"
                >
                  <i class="mdi mdi-chevron-down"></i>
                </button>
                <input
                  v-model.number="selectedModel"
                  type="number"
                  min="1"
                  class="border-t border-b border-gray-300 py-2 px-3 w-16 text-slate-700 focus:border-blue-400 focus:ring-2 focus:ring-blue-200 transition text-center text-base"
                  placeholder="Jumlah"
                />
                <button
                  type="button"
                  class="border rounded-r-lg py-2 px-3 text-center font-medium transition border-gray-300 hover:border-blue-400 text-slate-700 bg-gray-50 text-base"
                  @click="incrementModel"
                >
                  <i class="mdi mdi-chevron-up"></i>
                </button>
              </div>
            </div>
            <div class="mb-6">
              <!-- <h2 class="font-semibold text-lg mb-3">Kapasitas</h2> -->
              <div class="grid grid-cols-2 sm:grid-cols-4 gap-3">
                <button class="border rounded-lg py-3 px-4 text-center font-medium transition border-gray-300 hover:border-blue-400 text-slate-700 dark:text-white">Credit</button>
                <button class="border rounded-lg py-3 px-4 text-center font-medium transition border-gray-300 hover:border-blue-400 text-slate-700 dark:text-white">Bulanan</button>
                <button class="border rounded-lg py-3 px-4 text-center font-medium transition border-gray-300 hover:border-blue-400 text-slate-700 dark:text-white">Tahunan</button>
              </div>
            </div>
            <!-- Metode Pembayaran (dummy) -->
            <div class="mb-10">
              <h2 class="font-semibold text-lg mb-3">Pilihan Pembayaran</h2>
              <div class="grid grid-cols-2 sm:grid-cols-4 gap-3">
                <button class="border rounded-lg py-3 px-4 text-center font-medium transition border-gray-300 hover:border-blue-400 text-slate-700 flex items-center justify-center gap-2 dark:text-white">
                  <span>Rekber</span>
                </button>
                <button class="border rounded-lg py-3 px-4 text-center font-medium transition border-gray-300 hover:border-blue-400 text-slate-700 flex items-center justify-center gap-2 dark:text-white">
                  <img  :src="tokopedia" alt="Tokopedia" class="w-6 h-6" />
                  <span>Tokopedia</span>
                </button>
                <button class="border rounded-lg py-3 px-4 text-center font-medium transition border-gray-300 hover:border-blue-400 text-slate-700 flex items-center justify-center gap-2 dark:text-white">
                  <img :src="shopee" alt="Shopee" class="w-6 h-6" />
                  <span>Shopee</span>
                </button>
                <button class="border rounded-lg py-3 px-4 text-center font-medium transition border-gray-300 hover:border-blue-400 text-slate-700 flex items-center justify-center gap-2 dark:text-white">
                  <img :src="tiktok" alt="Tiktok" class="w-6 h-6" />
                  <span>Tiktok</span>
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
                  <span class="text-2xl leading-none dark:text-white">+</span>
                  <span class="dark:text-white">Keranjang</span>
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
                        <div class="grid grid-cols-1">
                            <div class="mb-4">
                                <label class="font-semibold" for="number3">Your Price:</label>
                                <input name="etherium" id="number3" type="number"
                                    class="form-input w-full text-[15px] py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-violet-600 dark:border-gray-800 dark:focus:border-violet-600 focus:ring-0 mt-3"
                                    placeholder="00.00 ETH">
                            </div>
                        </div>
                    </form>

                    <div class="pt-4 border-t dark:border-t-gray-800">
                        <div class="flex justify-between">
                            <p class="font-semibold text-sm"> You must bid at least:</p>
                            <p class="text-sm text-violet-600 font-semibold"> 1.22 ETH </p>
                        </div>
                        <div class="flex justify-between mt-1">
                            <p class="font-semibold text-sm"> Service free:</p>
                            <p class="text-sm text-violet-600 font-semibold"> 0.05 ETH </p>
                        </div>
                        <div class="flex justify-between mt-1">
                            <p class="font-semibold text-sm"> Total bid amount:</p>
                            <p class="text-sm text-violet-600 font-semibold"> 1.27 ETH </p>
                        </div>
                    </div>

                    <div class="flex items-center p-4 bg-red-600/10 text-red-600 mt-4 rounded-lg">
                        <i class="uil uil-exclamation-octagon text-3xl"></i>

                        <div class="ms-2">
                            <span class="block font-semibold">This creator is not verified</span>
                            <span class="block">Purchase this item at your own risk</span>
                        </div>
                    </div>

                    <div class="mt-4">
                        <a href="javascript:void(0)" data-modal-toggle="NftBuynow"
                            class="btn rounded-full bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white w-full"><i
                                class="mdi mdi-lightning-bolt"></i> Buy Now</a>
                    </div>
                </div>
            </div>
        </div>
      </div>
    </section>
    <switcher />
    <footers />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import navbar from '@/components/navbar/navbar.vue';
import switcher from '@/components/switcher.vue';
import footers from '@/components/footer/footer.vue'
import { useRoute } from 'vue-router';
import image from '../../assets/images/items/3.gif'
import avatarDefault from '@/assets/images/avatar/3.jpg'
import tokopedia from '@/assets/images/tokopedia.png'
import shopee from '@/assets/images/shopee.png'
import tiktok from '@/assets/images/tiktok.png'
import { useLicenseStore } from '@/stores/storeLicense'

const route = useRoute();
const id = ref(route.params.id)
const license = ref(null)
const isActive2 = ref(false)
const activeTab = ref('deskripsi')

const licenseStore = useLicenseStore()

const licenseImages = ref([
  '/images/produk1.jpg',
  '/images/produk2.jpg',
  '/images/produk3.jpg',
  '/images/produk4.jpg'
])

const selectedModel = ref(1)

const selectedImage = ref(licenseImages.value[0])

function prevImage() {
  let index = licenseImages.value.findIndex(img => img === selectedImage.value)
  if (index === -1) index = 0
  index = (index - 1 + licenseImages.value.length) % licenseImages.value.length
  selectedImage.value = licenseImages.value[index]
}

function nextImage() {
  let index = licenseImages.value.findIndex(img => img === selectedImage.value)
  if (index === -1) index = 0
  index = (index + 1) % licenseImages.value.length
  selectedImage.value = licenseImages.value[index]
}


function incrementModel() {
  selectedModel.value++
}
function decrementModel() {
  if (selectedModel.value > 1) selectedModel.value--
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
    license.value = await licenseStore.getDetailLicenses(id.value)
    // Ambil gambar utama dan gambar tambahan dari variabel image_url_1, image_url_2, dst
    const images = []
    if (license.value.image_url_1) images.push(license.value.image_url_1)
    if (license.value.image_url_2) images.push(license.value.image_url_2)
    if (license.value.image_url_3) images.push(license.value.image_url_3)
    if (license.value.image_url_4) images.push(license.value.image_url_4)
    licenseImages.value = images.length ? images : ['/images/produk1.jpg']
    selectedImage.value = licenseImages.value[0]
    // Set default condition to 'new' if not present
    if (!license.value.condition) {
      license.value.condition = 'new'
    }
  }
})
</script>

<style lang="scss" scoped></style>