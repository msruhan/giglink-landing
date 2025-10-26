<template>
    <div v-if="searchbar" class="lg:col-span-3">
        <!-- Mobile Only: Show only search field -->
        <form class="p-4 bg-white dark:bg-slate-900 rounded-xl shadow dark:shadow-gray-700 sticky top-[80px]">
            <div class="registration-form text-dark text-start">
                <div class="grid grid-cols-1 gap-6">
                    <div>
                        <label class="form-label font-semibold dark:text-white text-[15px]">Search:</label>
                        <div class="filter-search-form relative mt-2">
                        <div class="relative w-full">
                            <i class="uil uil-search icons absolute left-3 top-1/2 -translate-y-1/2 text-slate-400"></i>
                            <input name="name" type="text" id="job-keyword" class="form-input w-full filter-input-box bg-gray-50 dark:bg-slate-800 border-0 focus:ring-transparent pl-10 pr-32 rounded-lg" placeholder="Search your keywords">
                            <div class="absolute right-2 top-1/2 -translate-y-1/2 flex items-center">
                                <button type="button" class="flex items-center gap-2 px-3 py-2 bg-gray-100 dark:bg-slate-800 border border-gray-200 dark:border-slate-700 rounded-lg text-slate-700 dark:text-white focus:outline-none">
                                    <span>{{ selectedKota || 'Semua Kota' }}</span>
                                    <i class="uil uil-angle-down"></i>
                                </button>
                                <select v-model="selectedKota" class="absolute left-0 top-0 w-full h-full opacity-0 cursor-pointer">
                                    <option value="">Semua Kota</option>
                                    <option value="Jakarta">Jakarta</option>
                                    <option value="Bandung">Bandung</option>
                                    <option value="Surabaya">Surabaya</option>
                                    <option value="Yogyakarta">Yogyakarta</option>
                                    <option value="Medan">Medan</option>
                                    <option value="Semarang">Semarang</option>
                                    <option value="Makassar">Makassar</option>
                                    <option value="Palembang">Palembang</option>
                                    <option value="Denpasar">Denpasar</option>
                                    <option value="Balikpapan">Balikpapan</option>
                                    <option value="Pekanbaru">Pekanbaru</option>
                                    <option value="Malang">Malang</option>
                                    <option value="Batam">Batam</option>
                                    <option value="Padang">Padang</option>
                                    <option value="Samarinda">Samarinda</option>
                                    <option value="Pontianak">Pontianak</option>
                                    <option value="Banjarmasin">Banjarmasin</option>
                                    <option value="Manado">Manado</option>
                                    <option value="Cirebon">Cirebon</option>
                                </select>
                            </div>
                        </div>
                        </div>
                    </div>
                </div>
            </div>
        </form>
    </div>

    <div v-else class="lg:col-span-3">
        <div class="grid grid-cols-1">
            <!-- Mobile Only: Show only search field -->
            <form class="p-6 bg-white dark:bg-slate-900 rounded-xl shadow dark:shadow-gray-700">
                <div class="registration-form text-dark text-start">
                        <div class="grid grid-cols-1 gap-6">
                    <div>
                        <label class="form-label font-semibold dark:text-white text-[15px]">Search:</label>
                        <div class="filter-search-form relative mt-2">
                            <div class="relative w-full">
                                <i class="uil uil-search icons absolute left-3 top-1/2 -translate-y-1/2 text-slate-400"></i>
                                <input name="name" type="text" id="job-keyword" class="form-input w-full filter-input-box bg-gray-50 dark:bg-slate-800 border-0 focus:ring-transparent pl-10 pr-32 rounded-lg" placeholder="Search your keywords">
                                <div class="absolute right-2 top-1/2 -translate-y-1/2 flex items-center">
                                    <button type="button" class="flex items-center gap-2 px-3 py-2 bg-gray-100 dark:bg-slate-800 border border-gray-200 dark:border-slate-700 rounded-lg text-slate-700 dark:text-white focus:outline-none">
                                        <span>{{ selectedOnline || 'Online' }}</span>
                                        <i class="uil uil-angle-down"></i>
                                    </button>
                                    <select v-model="selectedOnline" class="absolute left-0 top-0 w-full h-full opacity-0 cursor-pointer">
                                        <option value="Online">Online</option>
                                        <option value="Offline">Offline</option>
                                    </select>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                </div>
            </form>
        </div>
    </div>
</template>

<script setup>
import { ref, defineProps } from 'vue'
const selectedKota = ref("");
const selectedOnline = ref("Online");
import vSelect from 'vue-select'
import 'vue-select/dist/vue-select.css'

defineProps({
    searchbar:{
        type: Boolean,
        required: true
    }
})

const options = ref(['Art', 'Music', 'Domain Names', 'Virtual World', 'Trading Cards', 'Sports'])
const selected = ref('Art')
const options2 = ref(['Buy Now', 'Auctions', 'Offers'])
const selected2 = ref('Buy Now')
const options3 = ref(['Top Rated', 'Lower Rated'])
const selected3 = ref('Top Rated')
</script>

<style lang="scss" scoped>

</style>