<template>
    <div>
        <div v-if="discover" class="container md:mt-24 mt-16">

        </div><!--end container-->
    
        <div v-else class="grid xl:grid-cols-4 lg:grid-cols-3 md:grid-cols-2 sm:grid-cols-2 grid-cols-2 mt-10 gap-[30px]">
            <div v-for="license in setlicenseData.slice(0, 4)" :key="license.id" class="group flex flex-col items-center">
              <div class="relative w-full rounded-2xl bg-white p-2 flex flex-col justify-between overflow-hidden">
                <!-- CARD ATAS (gambar produk) -->
                <div class="relative z-10 bg-gray-50 rounded-2xl overflow-hidden shadow-md">
                  <img :src="license.image_url_1" class="w-full h-48 object-cover rounded-2xl transition-transform duration-500 group-hover:scale-105" alt="license image" />
                </div>
                <!-- CARD BAWAH (judul, harga, fitur) -->
                <router-link :to="{name: 'details-license', params: {id: license.id}}" class="relative w-full rounded-2xl bg-gray-50 mt-4 text-left px-4 pb-6 pt-8 -mt-6 shadow-inner block group overflow-hidden">
                  <h3 class="text-md font-semibold text-gray-900 font-inter mb-3 mt-2">{{ license.title }}</h3>
                  <!-- Info Penjual -->
                  <div class="flex items-center space-x-3 mb-1">
                    <div class="relative">
                      <img src="/src/assets/images/avatar/3.jpg" class="h-5 w-5 rounded-full object-cover" alt="Foto Penjual">
                      <i class="mdi mdi-check-decagram text-emerald-600 text-md absolute -top-2 -end-2"></i>
                    </div>
                    <div class="flex items-center gap-2">
                      <span class="font-semibold text-xs text-slate-900 dark:text-white">{{ license.penjual || 'Penjual' }}</span>
                    </div>
                  </div>
                  <!-- Info Rating & Kondisi -->
                  <div class="flex flex-wrap items-center gap-2 text-xs text-slate-400 mb-3">
                    <i class="mdi mdi-eye"></i> {{ license.views || 0 }}x dilihat
                    <span class="flex items-center"><i class="mdi mdi-star text-yellow-400"></i> {{ license.rating || 0 }}/5</span>
                    <span v-if="license.license_type" :class="[ 'inline-block px-2 py-0.5 rounded-full text-xs font-semibold border', license.license_type === 'license' ? 'bg-emerald-500 text-white border-emerald-300' : license.license_type === 'credit' ? 'bg-yellow-100 text-yellow-700 border-yellow-300' : 'bg-gray-100 text-gray-700 border-gray-300' ]">
                      {{ license.license_type }}
                    </span>
                  </div>
                  <!-- BARIS BAWAH (Chat - Harga - Cart) -->
                  <div class="mt-2 text-gray-900 flex items-center justify-start w-full gap-2 ml-2">
                    <!-- Tombol Chat -->
                    <button class="flex items-center justify-center h-10 w-10 bg-white rounded-md shadow-sm border border-gray-200 text-sm font-semibold text-gray-900 transition hover:shadow-md shrink-0">
                      <i class="mdi mdi-message-text-outline text-lg text-gray-500"></i>
                    </button>
                    <!-- Harga -->
                    <div class="flex items-center justify-center flex-1 h-10 bg-white rounded-md shadow-sm border border-gray-200 text-sm font-bold text-gray-900 transition hover:shadow-md text-center">
                      {{ formatRupiah(license.price) }}
                    </div>
                    <!-- Tombol Cart -->
                    <button class="flex items-center justify-center h-10 w-10 bg-white rounded-md shadow-sm border border-gray-200 text-sm font-semibold text-gray-900 transition hover:shadow-md shrink-0">
                      <i class="mdi mdi-cart-outline text-lg text-gray-500"></i>
                    </button>
                  </div>
                  <span v-if="license.posting" class="text-xs text-slate-400 italic block mt-2">{{ license.posting }}</span>
                </router-link>
                <!-- BADGE OPTIONAL -->
                <span v-if="license.type === 'New'" class="absolute top-2 left-2 bg-gray-800 text-white text-xs font-medium px-3 py-1 rounded-full z-20">New</span>
              </div>
            </div><!--end content-->
        </div><!--end grid-->

        <div v-if="moreitem" class="grid grid-cols-1 mt-6">
            <div class="text-center">
                <router-link to="/explore-one" class="btn btn-link text-[16px] font-medium hover:text-violet-600 after:bg-violet-600 duration-500 ease-in-out">Explore More <i class="uil uil-arrow-right"></i></router-link>
            </div>
        </div><!--end grid-->
    </div>
</template>

<script>
import { useLicenseStore } from '@/stores/storeLicense'
export default {
    props: {
        discover: {
            type: Boolean,
            required: true
        },
        items: {
            type: Boolean,
            required: true
        },
        moreitem: {
            type: Boolean,
            required: true
        },
        explore: {
            type: Boolean,
            required: true
        },
    },
    name: "ExploreOne",
    data() {
        return {
            setlicenseData: [],
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
    },
    beforeUnmount() {
        clearInterval(this._interval)
    },
    methods: {
        tickTock(date) {
            let startDate = new Date(date);
            let currentDate = new Date();
            const diff = startDate.getTime() - currentDate.getTime();
            const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((diff / (1000 * 60)) % 60);
            const seconds = Math.floor((diff / 1000) % 60);
            const days = Math.floor(diff / (1000 * 60 * 60 * 24));
            return { hours, minutes, seconds, days }
        },
        setPostingInfo() {
            const now = new Date();
            this.setlicenseData = this.setlicenseData.map(item => {
                if (!item.postingDate) return item;
                const postingDate = new Date(item.postingDate);
                const diffTime = now - postingDate;
                const diffDays = Math.floor(diffTime / (1000 * 60 * 60 * 24));
                let posting = '';
                if (diffDays === 0) {
                    posting = 'Iklan diposting hari ini';
                } else if (diffDays === 1) {
                    posting = 'Iklan diposting 1 hari yang lalu';
                } else {
                    posting = `Iklan diposting ${diffDays} hari yang lalu`;
                }
                return { ...item, posting };
            });
        },
        formatRupiah(value) {
            if (!value) return 'Rp0';
            return 'Rp' + value.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
        },
    }
}
</script>

<style lang="scss" scoped></style>