<template>
  <div class="container mx-auto py-8">
    <div class="flex flex-col lg:flex-row gap-8">
      <!-- Main Content -->
      <div class="flex-1">
        <!-- Profile Card -->
        <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6 flex flex-col md:flex-row gap-6 items-center">
        <img
          :src="technician?.image_url || imageSrc2"
          class="w-32 h-32 rounded-full object-cover border-4 border-violet-600 shadow"
          alt="Profile"
        />
          <div class="flex-1 text-center md:text-left">
           <h2 class="text-2xl font-bold flex items-center justify-center md:justify-start gap-2">
              {{ technician?.display_name || '-' }}
              <i class="mdi mdi-check-decagram text-emerald-600 text-xl"></i>
           </h2>
            <p class="text-slate-500 text-lg">  {{ technician?.title || '-' }}</p>
            <div class="flex flex-wrap justify-center md:justify-start gap-4 mt-2 text-slate-400 text-sm">
              <span class="flex items-center gap-1"><i class="mdi mdi-map-marker"></i>{{ technician?.location || '-' }}</span>
              <span class="flex items-center gap-1"><i class="mdi mdi-calendar"></i>{{ formatTanggal(technician?.created_at) }}</span>
              <span class="flex items-center gap-1"><i class="mdi mdi-star"></i>{{ technician?.rating || '-' }} (245 Reviews)</span>
            </div>
            <div class="flex flex-wrap gap-2 mt-4 justify-center md:justify-start">
              <button class="btn btn-sm rounded-full bg-violet-600 hover:bg-violet-700 text-white"><i class="mdi mdi-plus"></i> Follow me</button>
              <!-- <button class="btn btn-icon btn-sm rounded-full bg-violet-600 hover:bg-violet-700 text-white"><i class="mdi mdi-account-plus"></i></button> -->
              <!-- <router-link to="/creator-profile-edit" class="btn btn-icon btn-sm rounded-full bg-violet-100 hover:bg-violet-600 text-violet-600 hover:text-white"><i class="mdi mdi-cog"></i></router-link> -->
              <!-- Social Media Icons -->
              <a :href="technician?.youtube || '#'" class="btn btn-icon btn-sm rounded-full bg-red-600 hover:bg-red-700 text-white" title="Youtube" target="_blank" rel="noopener"><i class="mdi mdi-youtube"></i></a>
              <a :href="technician?.instagram || '#'" class="btn btn-icon btn-sm rounded-full bg-gradient-to-tr from-purple-600 to-yellow-400 hover:from-pink-600 hover:to-yellow-600 text-white" title="Instagram" target="_blank" rel="noopener"><i class="mdi mdi-instagram"></i></a>
              <a :href="technician?.facebook || '#'" class="btn btn-icon btn-sm rounded-full bg-blue-600 hover:bg-blue-800 text-white" title="Facebook" target="_blank" rel="noopener"><i class="mdi mdi-facebook"></i></a>
              <a :href="technician?.whatsapp || '#'" class="btn btn-icon btn-sm rounded-full bg-green-500 hover:bg-green-700 text-white" title="WhatsApp" target="_blank" rel="noopener"><i class="mdi mdi-whatsapp"></i></a>
            </div>
          </div>
        </div>

        <!-- Stats -->
        <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-4 mt-6">
          <div class="bg-violet-50 dark:bg-slate-800 rounded-lg p-4 flex flex-col items-center">
            <span class="mdi mdi-thumb-up text-4xl text-violet-600 mb-2"></span>
            <div class="flex flex-col items-center">
              <span class="font-bold text-lg mt-1 text-center">89%</span>
              <span class="text-xs text-slate-400 text-center">Recommended</span>
            </div>
          </div>
          <div class="bg-violet-50 dark:bg-slate-800 rounded-lg p-4 flex flex-col items-center">
            <span class="mdi mdi-briefcase-check text-4xl text-violet-600 mb-2"></span>
            <div class="flex flex-col items-center">
              <span class="font-bold text-lg mt-1 text-center">220</span>
              <span class="text-xs text-slate-400 text-center">Completed Projects</span>
            </div>
          </div>
          <div class="bg-violet-50 dark:bg-slate-800 rounded-lg p-4 flex flex-col items-center">
            <span class="mdi mdi-progress-clock text-4xl text-violet-600 mb-2"></span>
            <div class="flex flex-col items-center">
              <span class="font-bold text-lg mt-1 text-center">10</span>
              <span class="text-xs text-slate-400 text-center">Ongoing Projects</span>
            </div>
          </div>
          <div class="bg-violet-50 dark:bg-slate-800 rounded-lg p-4 flex flex-col items-center">
            <span class="mdi mdi-account-heart text-4xl text-violet-600 mb-2"></span>
            <div class="flex flex-col items-center">
              <span class="font-bold text-lg mt-1 text-center">78</span>
              <span class="text-xs text-slate-400 text-center">Feedbacks</span>
            </div>
          </div>
          <div class="bg-violet-50 dark:bg-slate-800 rounded-lg p-4 flex flex-col items-center">
            <span class="mdi mdi-repeat text-4xl text-violet-600 mb-2"></span>
            <div class="flex flex-col items-center">
              <span class="font-bold text-lg mt-1 text-center">Rehired</span>
              <span class="text-xs text-slate-400 text-center">Rehired</span>
            </div>
          </div>
          <div class="bg-violet-50 dark:bg-slate-800 rounded-lg p-4 flex flex-col items-center">
            <span class="mdi mdi-timer text-4xl text-violet-600 mb-2"></span>
            <div class="flex flex-col items-center">
              <span class="font-bold text-lg mt-1 text-center">1 Hour</span>
              <span class="text-xs text-slate-400 text-center">Response Times</span>
            </div>
          </div>
        </div>

        <!-- Description -->
        <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6 mt-6">
          <h3 class="text-xl font-bold mb-2">Tentang Kami</h3>
          <p class="text-slate-500 mb-2">{{ technician?.description || '-' }}</p>
        </div>

        <!-- Experience -->
        <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6 mt-6">
          <h3 class="text-xl font-bold mb-4">Experience</h3>
          <div class="space-y-4">
            <div class="flex gap-4 items-start">
              <img :src="imageSrc2" class="w-12 h-12 rounded-full object-cover" alt="Experience" />
              <div>
                <h4 class="font-semibold">Team Leader <span class="text-xs text-slate-400 ml-2">2017 - 2023</span></h4>
                <span class="block text-slate-400 text-sm">UI UX Designer</span>
                <p class="text-slate-500 text-sm">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
              </div>
            </div>
            <div class="flex gap-4 items-start">
              <img :src="imageSrc2" class="w-12 h-12 rounded-full object-cover" alt="Experience" />
              <div>
                <h4 class="font-semibold">Senior UI UX Designer <span class="text-xs text-slate-400 ml-2">2019 - 2021</span></h4>
                <span class="block text-slate-400 text-sm">UI UX Designer</span>
                <p class="text-slate-500 text-sm">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
              </div>
            </div>
            <div class="flex gap-4 items-start">
              <img :src="imageSrc2" class="w-12 h-12 rounded-full object-cover" alt="Experience" />
              <div>
                <h4 class="font-semibold">Junior UI UX Designer <span class="text-xs text-slate-400 ml-2">2016 - 2019</span></h4>
                <span class="block text-slate-400 text-sm">UI UX Designer</span>
                <p class="text-slate-500 text-sm">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
              </div>
            </div>
          </div>
        </div>

        <!-- Education -->
        <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6 mt-6">
          <h3 class="text-xl font-bold mb-4">Education</h3>
          <div class="space-y-4">
            <div class="flex gap-4 items-start">
              <img :src="imageSrc2" class="w-12 h-12 rounded-full object-cover" alt="Education" />
              <div>
                <h4 class="font-semibold">Master Degree <span class="text-xs text-slate-400 ml-2">2013 - 2016</span></h4>
                <span class="block text-slate-400 text-sm">Arizona State University</span>
                <p class="text-slate-500 text-sm">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
              </div>
            </div>
            <div class="flex gap-4 items-start">
              <img :src="imageSrc2" class="w-12 h-12 rounded-full object-cover" alt="Education" />
              <div>
                <h4 class="font-semibold">Bachelor Degree <span class="text-xs text-slate-400 ml-2">2010 - 2013</span></h4>
                <span class="block text-slate-400 text-sm">Arizona State University</span>
                <p class="text-slate-500 text-sm">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
              </div>
            </div>
          </div>
        </div>

        <!-- Reviews -->
        <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6 mt-6">
          <h3 class="text-xl font-bold mb-4">Review (5)</h3>
          <div class="space-y-6">
            <div class="flex gap-4 items-start">
              <img :src="imageSrc2" class="w-12 h-12 rounded-full object-cover" alt="Education" />
              <div class="flex-1">
                <div class="flex flex-wrap justify-between items-center">
                  <div>
                    <h4 class="font-semibold">Theresa Phillips</h4>
                    <div class="flex gap-4 text-xs text-slate-400 mt-1">
                      <span><i class="mdi mdi-star"></i> 5.0 (346 Reviews)</span>
                      <span><i class="mdi mdi-calendar"></i> 1 min ago</span>
                    </div>
                  </div>
                  <div class="text-right">
                    <div class="font-bold text-lg">$40-$500</div>
                    <span class="text-xs text-slate-400">Price : Fixed</span>
                  </div>
                </div>
                <p class="text-slate-500 mt-2">I've been buying and selling on kofejob Marketplace for the past two years, and it's been a game-changer for me. The platform is user-friendly, and I've had great success selling my handmade crafts. Plus, the customer support team is always there to help if I have any questions or issues.</p>
              </div>
            </div>
            <!-- Repeat for other reviews as needed -->
          </div>
        </div>
      </div>

      <!-- Sidebar -->
      <div class="w-full lg:w-80 flex-shrink-0 space-y-6">
        <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6">
          <h4 class="font-bold text-lg mb-2">Budget</h4>
          <div class="text-2xl font-bold text-violet-600 mb-1">$125 - $180</div>
          <div class="text-slate-400 text-sm mb-4">Hourly Rate</div>
          <ul class="space-y-2 text-sm">
            <li class="flex items-center gap-2"><i class="mdi mdi-map-marker"></i> <span>{{ technician?.location || '-' }}</span></li>
            <li class="flex items-center gap-2"><i class="mdi mdi-briefcase"></i> <span>{{ technician?.experience_years || '-' }} Years Experience</span></li>
            <li class="flex items-center gap-2"><i class="mdi mdi-calendar"></i> <span>Delivery: 3-5 Days</span></li>
            <li class="flex items-center gap-2"><i class="mdi mdi-web"></i> <span>Language: Basic</span></li>
            <li class="flex items-center gap-2"><i class="mdi mdi-phone"></i> <span>{{ technician?.whatsapp || '-' }}</span></li>
            <li class="flex items-center gap-2"><i class="mdi mdi-email"></i> <span>{{ technician?.email || '-' }}</span></li>
          </ul>
          <router-link :to="{name: 'creator-chat'}" class="btn btn-primary w-full mt-4"> Hubungi</router-link>
        </div>
        <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6">
          <h4 class="font-bold text-lg mb-2">Skills</h4>
          <div v-if="technician?.skills && technician?.skills.length" class="flex flex-wrap items-center gap-2 mt-2">
              <span
                v-for="(skill, idx) in (Array.isArray(technician.skills) ? technician.skills : technician.skills.split(','))"
                :key="idx"
                class="px-2 py-0.5 rounded-full bg-violet-100 text-violet-700 text-xs font-medium border border-violet-200"
               >
                {{ skill.trim() }}
              </span>
          </div>
        </div>
        <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6">
          <h4 class="font-bold text-lg mb-2">Location</h4>
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
import { useTechnicianStore } from '@/stores/storeTechnician'

const props = defineProps({ id: [String, Number] })
const technicianStore = useTechnicianStore()
const technician = ref(null)
const imageSrc2 = ref(images2)

const fetchTechnician = async () => {
  technician.value = await technicianStore.getDetailTechnicians(props.id)
}

onMounted(fetchTechnician)
watch(() => props.id, fetchTechnician)

// Fungsi format tanggal ke "14 Oktober 2025"
function formatTanggal(dateStr) {
  if (!dateStr) return '-'
  const bulan = [
    'Januari', 'Februari', 'Maret', 'April', 'Mei', 'Juni',
    'Juli', 'Agustus', 'September', 'Oktober', 'November', 'Desember'
  ]
  const d = new Date(dateStr)
  if (isNaN(d)) return '-'
  return `${d.getDate()} ${bulan[d.getMonth()]} ${d.getFullYear()}`
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