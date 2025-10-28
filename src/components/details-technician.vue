<template>
  <div class="bg-[#f4f4f4] text-[#1a1a1a] min-h-screen font-inter">
    <div class="container mx-auto py-8">
      <div class="flex flex-col lg:flex-row gap-8">
        <!-- Main Content -->
        <div class="flex-1">
          <!-- ================= PROFILE CARD ================= -->
          <!-- Profile Card Modern -->
          <div class="bg-gradient-to-r from-black via-emerald-700 to-green-400 rounded-2xl shadow-lg p-8 flex flex-col md:flex-row gap-8 items-center relative overflow-hidden">
            <img
              :src="technician?.image_url || imageSrc2"
              class="w-40 h-40 object-cover border-4 border-white shadow-xl rounded-2xl bg-white"
              alt="Profile"
            />
            <div class="flex-1 text-center md:text-left text-white font-inter">
              <h2 class="text-3xl font-extrabold flex items-center justify-center md:justify-start gap-2 font-inter">
                {{ technician?.display_name || '-' }}
                <i class="mdi mdi-check-decagram text-emerald-300 text-2xl"></i>
              </h2>
              <p class="text-emerald-100 text-lg mt-1 font-inter">{{ technician?.title || 'Teknisi Smartphone Profesional' }}</p>
              <div class="flex flex-wrap justify-center md:justify-start gap-4 mt-2 text-emerald-200 text-sm font-inter">
                <span class="flex items-center gap-1"><i class="mdi mdi-map-marker"></i> {{ technician?.location || '-' }}</span>
                <span class="flex items-center gap-1"><i class="mdi mdi-calendar"></i> {{ formatTanggal(technician?.created_at) }}</span>
                <span class="flex items-center gap-1"><i class="mdi mdi-star"></i> {{ technician?.rating || '-' }} (245 Reviews)</span>
              </div>
              <div class="flex flex-wrap gap-2 mt-4 justify-center md:justify-start font-inter">
                <button class="btn btn-sm rounded-full bg-white text-violet-700 hover:bg-violet-100 font-bold font-inter"><i class="mdi mdi-plus"></i> Follow</button>
                <a :href="technician?.youtube || '#'" class="btn btn-icon btn-sm rounded-full bg-red-600 hover:bg-red-700 text-white font-inter" title="Youtube" target="_blank"><i class="mdi mdi-youtube"></i></a>
                <a :href="technician?.instagram || '#'" class="btn btn-icon btn-sm rounded-full bg-gradient-to-tr from-purple-600 to-yellow-400 hover:from-pink-600 hover:to-yellow-600 text-white font-inter" title="Instagram" target="_blank"><i class="mdi mdi-instagram"></i></a>
                <a :href="technician?.facebook || '#'" class="btn btn-icon btn-sm rounded-full bg-blue-600 hover:bg-blue-800 text-white font-inter" title="Facebook" target="_blank"><i class="mdi mdi-facebook"></i></a>
                <a :href="technician?.whatsapp || '#'" class="btn btn-icon btn-sm rounded-full bg-green-500 hover:bg-green-700 text-white font-inter" title="WhatsApp" target="_blank"><i class="mdi mdi-whatsapp"></i></a>
              </div>
            </div>
          </div>

          <!-- ================= STATS ================= -->
          <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 mt-6 items-stretch">
            <div v-for="(item, i) in stats" :key="i" class="bg-white dark:bg-slate-900 rounded-xl p-4 flex flex-col items-center h-full">
              <span :class="item.icon + ' text-4xl text-emerald-500 mb-2'"></span>
              <div class="flex flex-col items-center flex-1 justify-center">
                <span class="font-bold text-lg mt-1 text-center">{{ item.value }}</span>
                <span class="text-xs text-slate-400 text-center">{{ item.label }}</span>
              </div>
            </div>
          </div>

          <!-- ================= TENTANG TEKNISI ================= -->
          <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6 mt-6">
            <h3 class="text-xl font-bold mb-2">Tentang Saya</h3>
            <p class="text-slate-500 mb-2">
              {{ technician?.description || 'Lebih dari 6 tahun pengalaman dalam perbaikan software dan hardware smartphone berbagai merek. Menguasai alat servis profesional seperti UFI Box, Pandora, dan EasyJTAG.' }}
            </p>
          </div>

          <!-- ================= NEW SECTION: LAYANAN ================= -->
          <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6 mt-6">
            <h3 class="text-xl font-bold mb-4">Layanan Tersedia</h3>
            <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-4">
              <div v-for="(service, idx) in services" :key="idx" class="relative border border-emerald-200 dark:border-violet-700 rounded-2xl p-5 bg-white/70 dark:bg-slate-800/80 backdrop-blur-md shadow-lg hover:scale-[1.04] hover:shadow-2xl transition-all duration-300 flex flex-col h-full overflow-hidden">
                <!-- Ribbon label -->
                <div class="absolute top-0 left-0 bg-emerald-600 text-white text-xs font-bold px-3 py-1 rounded-br-xl shadow-lg z-10">Service</div>
                <div class="flex items-center gap-3 mb-2 mt-2">
                  <span class="inline-flex items-center justify-center w-12 h-12 rounded-xl bg-gradient-to-tr from-emerald-200 to-emerald-400 text-emerald-700 text-3xl shadow-lg"><i :class="service.icon"></i></span>
                  <h4 class="font-semibold text-emerald-700 text-lg">{{ service.name }}</h4>
                </div>
                <p class="text-sm text-slate-500 flex-1 mt-2">{{ service.desc }}</p>
              </div>
            </div>
          </div>

          <!-- ================= NEW SECTION: GALERI ================= -->
          <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6 mt-6">
            <h3 class="text-xl font-bold mb-4">Galeri Teknisi</h3>
            <p class="text-slate-500 mb-6">Foto hasil pekerjaan dan suasana di workshop kami.</p>

            <!-- Galeri Hasil Pekerjaan -->
            <h4 class="text-lg font-semibold mb-3 flex items-center gap-2">
              <i class="mdi mdi-hammer-wrench text-emerald-600"></i> Hasil Pekerjaan
            </h4>
            <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-4 mb-6">
              <template v-if="galleryWork && galleryWork.length">
                <img
                  v-for="(img, i) in galleryWork"
                  :key="'work-' + i"
                  :src="img"
                  class="rounded-lg object-cover aspect-video hover:scale-105 transition shadow-sm"
                  alt="Hasil Servis"
                />
              </template>
              <template v-else>
                <img v-for="i in 3" :key="'work-dummy-' + i" src="https://via.placeholder.com/400x225?text=Foto+Hasil+Dummy" class="rounded-lg object-cover aspect-video hover:scale-105 transition shadow-sm" alt="Dummy Hasil Servis" />
              </template>
            </div>

            <!-- Galeri Workshop -->
            <h4 class="text-lg font-semibold mb-3 flex items-center gap-2">
              <i class="mdi mdi-store-outline text-emerald-600"></i> Galeri Toko / Workshop
            </h4>
            <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-4">
              <template v-if="galleryShop && galleryShop.length">
                <img
                  v-for="(img, i) in galleryShop"
                  :key="'shop-' + i"
                  :src="img"
                  class="rounded-lg object-cover aspect-video hover:scale-105 transition shadow-sm"
                  alt="Workshop"
                />
              </template>
              <template v-else>
                <img v-for="i in 3" :key="'shop-dummy-' + i" src="https://via.placeholder.com/400x225?text=Foto+Workshop+Dummy" class="rounded-lg object-cover aspect-video hover:scale-105 transition shadow-sm" alt="Dummy Workshop" />
              </template>
            </div>
          </div>


          <!-- ================= NEW SECTION: RIWAYAT SERVIS ================= -->
          <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6 mt-6 overflow-x-auto">
            <h3 class="text-xl font-bold mb-4">Riwayat Servis Terbaru</h3>
            <table class="min-w-full text-sm text-left border-collapse">
              <thead>
                <tr class="border-b border-slate-200 dark:border-slate-700">
                  <th class="py-2 px-3">Tanggal</th>
                  <th class="py-2 px-3">Jenis Pekerjaan</th>
                  <th class="py-2 px-3">Model HP</th>
                  <th class="py-2 px-3">Status</th>
                  <th class="py-2 px-3">Feedback</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="(item, i) in history" :key="i" class="border-b border-slate-100 dark:border-slate-800">
                  <td class="py-2 px-3">{{ item.date }}</td>
                  <td class="py-2 px-3">{{ item.job }}</td>
                  <td class="py-2 px-3">{{ item.model }}</td>
                  <td class="py-2 px-3"><span class="px-2 py-0.5 rounded-full bg-green-100 text-green-600 text-xs">{{ item.status }}</span></td>
                  <td class="py-2 px-3">{{ item.feedback }}</td>
                </tr>
              </tbody>
            </table>
          </div>

          <!-- ================= REVIEW ================= -->
          <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6 mt-6">
            <h3 class="text-xl font-bold mb-4">Ulasan Pelanggan</h3>
            <div class="space-y-6">
              <div v-for="(review, i) in reviews" :key="i" class="flex gap-4 items-start">
                <img :src="review.avatar || imageSrc2" class="w-12 h-12 rounded-full object-cover" alt="Reviewer" />
                <div class="flex-1">
                  <div class="flex justify-between items-center">
                    <h4 class="font-semibold">{{ review.name }}</h4>
                    <span class="text-xs text-slate-400">{{ review.date }}</span>
                  </div>
                  <p class="text-sm text-slate-500 mt-1">{{ review.comment }}</p>
                  <div v-if="review.photo" class="mt-2">
                    <img :src="review.photo" alt="Foto Ulasan" class="rounded-lg w-32 h-20 object-cover border border-slate-200" />
                  </div>
                  <div class="text-xs text-yellow-500 mt-1"><i class="mdi mdi-star" v-for="n in review.rating" :key="n"></i></div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- ================= SIDEBAR ================= -->
        <div class="w-full lg:w-80 flex-shrink-0 space-y-6">
          <!-- Sidebar info existing -->
          <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6">
            <h4 class="font-bold text-lg mb-2">Budget</h4>
            <div class="text-2xl font-bold text-emerald-600 mb-1">$125 - $180</div>
            <div class="text-slate-400 text-sm mb-4">Hourly Rate</div>
            <ul class="space-y-2 text-sm">
              <li class="flex items-center gap-2"><i class="mdi mdi-map-marker"></i> <span>{{ technician?.location || '-' }}</span></li>
              <li class="flex items-center gap-2"><i class="mdi mdi-briefcase"></i> <span>{{ technician?.experience_years || '6' }} Years Experience</span></li>
              <li class="flex items-center gap-2"><i class="mdi mdi-calendar"></i> <span>Delivery: 3-5 Days</span></li>
              <li class="flex items-center gap-2"><i class="mdi mdi-web"></i> <span>Language: Basic</span></li>
              <li class="flex items-center gap-2"><i class="mdi mdi-phone"></i> <span>{{ technician?.whatsapp || '-' }}</span></li>
              <li class="flex items-center gap-2"><i class="mdi mdi-email"></i> <span>{{ technician?.email || '-' }}</span></li>
            </ul>
            <router-link :to="{name: 'creator-chat'}" class="btn bg-emerald-500 hover:bg-emerald-700 text-white font-inter w-full mt-4 rounded-full shadow transition font-semibold"> Hubungi</router-link>
          </div>

          <!-- Skills existing -->
          <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6">
            <h4 class="font-bold text-lg mb-2">Skills</h4>
            <div class="flex flex-wrap items-center gap-2 mt-2">
              <span v-for="(skill, idx) in skills" :key="idx" class="px-2 py-0.5 rounded-full bg-emerald-100 text-emerald-700 text-xs font-medium border border-emerald-200">
                {{ skill }}
              </span>
            </div>
          </div>

          <!-- Location existing -->
          <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6">
            <h4 class="font-bold text-lg mb-2">Lokasi</h4>
            <div class="aspect-video rounded-lg overflow-hidden mb-4">
              <iframe src="https://www.google.com/maps/embed?pb=!1m16..." width="100%" height="200" style="border:0;" allowfullscreen="" loading="lazy"></iframe>
            </div>
            <div class="space-y-2 text-sm">
              <div class="flex items-center gap-2">
                <i class="mdi mdi-map-marker-radius text-emerald-600"></i>
                <span>Radius layanan antar jemput: <b>10 km</b> dari Toko</span>
              </div>
              <div class="flex items-center gap-2">
                <i class="mdi mdi-clock-outline text-emerald-600"></i>
                <span>Jadwal buka: <b>Senin–Sabtu, 09.00–17.00</b></span>
              </div>
            </div>
          </div>


          <!-- Certification Card -->
          <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6">
            <div class="card-body">
              <h5 class="text-lg font-semibold mb-3">Sertifikasi</h5>

              <ul class="space-y-3">
                <li class="flex items-start gap-3">
                  <div class="w-8 h-8 flex items-center justify-center bg-purple-100 rounded-full text-purple-600">
                    <i class="fa-solid fa-certificate"></i>
                  </div>
                  <div>
                    <p class="font-medium">UFI Box Certified Technician</p>
                    <p class="text-sm text-gray-500">UFI Team Indonesia · 2024</p>
                  </div>
                </li>

                <li class="flex items-start gap-3">
                  <div class="w-8 h-8 flex items-center justify-center bg-purple-100 rounded-full text-purple-600">
                    <i class="fa-solid fa-microchip"></i>
                  </div>
                  <div>
                    <p class="font-medium">Board Level Repair Training</p>
                    <p class="text-sm text-gray-500">Pandora Workshop · 2023</p>
                  </div>
                </li>

                <li class="flex items-start gap-3">
                  <div class="w-8 h-8 flex items-center justify-center bg-purple-100 rounded-full text-purple-600">
                    <i class="fa-solid fa-mobile-screen"></i>
                  </div>
                  <div>
                    <p class="font-medium">Smartphone Software Reprogramming</p>
                    <p class="text-sm text-gray-500">MRT Dongle Academy · 2022</p>
                  </div>
                </li>
              </ul>
            </div>
          </div>
          
          <!-- Konsultasi Gratis Card -->
          <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6">
            <h4 class="font-bold text-lg mb-2 flex items-center gap-2">
              <i class="mdi mdi-message-question text-emerald-600 text-xl"></i>
              Konsultasi Gratis
            </h4>
            <p class="text-slate-500 mb-3">Ada masalah di HP kamu? Jelaskan gejalanya — saya bantu diagnosa gratis.</p>
            <form @submit.prevent="onConsultSubmit" class="space-y-3">
              <textarea class="w-full rounded-lg border border-emerald-200 dark:border-slate-700 p-2 text-sm" rows="3" placeholder="Ceritakan masalah HP kamu..." v-model="consultMessage"></textarea>
              <button type="submit" class="btn bg-emerald-500 hover:bg-emerald-700 text-white font-inter w-full mt-4 rounded-full shadow transition font-semibold">
                <i class="mdi mdi-chat-processing-outline"></i> Konsultasi Sekarang
              </button>
            </form>
          </div>

        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import images2 from '../assets/images/avatar/1.jpg'
import { ref, onMounted, watch } from 'vue'
import { useTechnicianStore } from '@/stores/storeTechnician'

const props = defineProps({ id: [String, Number] })
const technicianStore = useTechnicianStore()
const technician = ref(null)
const imageSrc2 = ref(images2)

// Dummy data for new sections
const stats = [
  { icon: 'mdi mdi-thumb-up', value: '89%', label: 'Recommended' },
  { icon: 'mdi mdi-briefcase-check', value: '220', label: 'Completed Jobs' },
  { icon: 'mdi mdi-account-heart', value: '78', label: 'Feedbacks' },
  { icon: 'mdi mdi-timer', value: '1 Hour', label: 'Response Time' },
]

const services = [
  { name: 'Ganti IC Power', desc: 'Perbaikan IC power dan charging berbagai tipe HP.', time: '1-2 Hari', price: 'Rp 200.000 - 400.000', icon: 'mdi mdi-lightning-bolt' },
  { name: 'Flashing / Software', desc: 'Install ulang sistem HP yang bootloop / hang logo.', time: '2 Jam', price: 'Rp 100.000 - 250.000', icon: 'mdi mdi-cellphone-arrow-down' },
  { name: 'Ganti LCD', desc: 'Penggantian layar rusak atau retak berbagai merek.', time: '1 Hari', price: 'Rp 300.000 - 1.000.000', icon: 'mdi mdi-cellphone' },
  { name: 'Unlock / FRP', desc: 'Membuka kunci pola, PIN, atau akun Google (FRP).', time: '1 Jam', price: 'Rp 150.000 - 250.000', icon: 'mdi mdi-lock-open' },
  { name: 'Ganti Baterai', desc: 'Ganti baterai drop atau kembung untuk iPhone & Android.', time: '1 Jam', price: 'Rp 120.000 - 250.000', icon: 'mdi mdi-battery' },
  { name: 'Data Recovery', desc: 'Pemulihan data penting dari HP mati total.', time: '1-3 Hari', price: 'Mulai Rp 300.000', icon: 'mdi mdi-database-refresh' },
]

const galleryWork = [
  '/images/work1.jpg', '/images/work2.jpg', '/images/work3.jpg'
]
const galleryShop = [
  '/images/shop1.jpg', '/images/shop2.jpg', '/images/shop3.jpg'
]

const history = [
  { date: '15 Okt 2025', job: 'Ganti IC Power', model: 'Samsung A12', status: 'Selesai', feedback: '⭐⭐⭐⭐⭐' },
  { date: '12 Okt 2025', job: 'Flashing ROM', model: 'Xiaomi Redmi 9', status: 'Selesai', feedback: '⭐⭐⭐⭐' },
  { date: '10 Okt 2025', job: 'Bypass FRP', model: 'Oppo A5', status: 'Selesai', feedback: '⭐⭐⭐⭐⭐' },
]

const reviews = [
  {
    name: 'Theresa Phillips',
    comment: 'HP saya mati total, tapi berhasil nyala lagi. Cepat dan rapi banget!',
    rating: 5,
    date: '2 hari lalu',
    avatar: 'https://randomuser.me/api/portraits/women/44.jpg',
    photo: 'https://images.unsplash.com/photo-1519125323398-675f0ddb6308?auto=format&fit=crop&w=400&q=80'
  },
  {
    name: 'Rahman D.',
    comment: 'Service cepat, komunikatif, dan hasil memuaskan.',
    rating: 5,
    date: '5 hari lalu',
    avatar: 'https://randomuser.me/api/portraits/men/32.jpg'
  },
]


const consultMessage = ref('')
function onConsultSubmit() {
  if (!consultMessage.value.trim()) {
    alert('Silakan isi gejala masalah HP Anda.');
    return
  }
  alert('Terima kasih! Pesan konsultasi Anda telah dikirim.');
  consultMessage.value = ''
}

const skills = ['Android', 'iPhone', 'Flashing', 'LCD Repair', 'Battery Replacement']

const fetchTechnician = async () => {
  technician.value = await technicianStore.getDetailTechnicians(props.id)
}

onMounted(fetchTechnician)
watch(() => props.id, fetchTechnician)

function formatTanggal(dateStr) {
  if (!dateStr) return '-'
  const bulan = ['Januari','Februari','Maret','April','Mei','Juni','Juli','Agustus','September','Oktober','November','Desember']
  const d = new Date(dateStr)
  if (isNaN(d)) return '-'
  return `${d.getDate()} ${bulan[d.getMonth()]} ${d.getFullYear()}`
}
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap');

.font-inter {
  font-family: 'Inter', sans-serif;
}

.shadow-md {
  box-shadow: 0 6px 18px rgba(0, 0, 0, 0.05);
}

.ring-gray-100 {
  --tw-ring-color: rgba(0, 0, 0, 0.05);
}

.btn {
  @apply px-4 py-2 rounded-full font-semibold shadow transition;
}
.btn-primary {
  @apply bg-violet-600 hover:bg-violet-700 text-white;
}
</style>
