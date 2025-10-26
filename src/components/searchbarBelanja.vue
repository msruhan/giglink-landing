<template>
    <div v-if="searchbar" class="lg:col-span-3">
        <!-- Mobile Only: Show only search field -->
        <form class="p-4 bg-white dark:bg-slate-900 rounded-xl shadow dark:shadow-gray-700 sticky top-[80px]">
            <div class="registration-form text-dark text-start">
                <div class="grid grid-cols-1 gap-6">
                    <div>
                        <label class="form-label font-semibold dark:text-white text-[15px]">Search:</label>
                        <div class="filter-search-form relative mt-2">
                            <i class="uil uil-search icons"></i>
                            <input name="name" type="text" id="job-keyword" class="form-input w-full filter-input-box bg-gray-50 dark:bg-slate-800 border-0 focus:ring-transparent" placeholder="Search your keaywords">
                        </div>
                    </div>
                </div>
            </div>
        </form>
    </div>



    <div v-else class="container z-1">
        <div class="grid grid-cols-1">
            <!-- Mobile Only: Show only search field -->
            <form class="p-6 bg-white dark:bg-slate-900 rounded-xl shadow dark:shadow-gray-700">
                <div class="registration-form text-dark text-start">
                    <div class="grid grid-cols-1 gap-6">
                        <div>
                            <label class="form-label font-medium dark:text-white">Search:</label>
                            <div class="filter-search-form relative filter-border mt-2">
                                <i class="uil uil-search icons"></i>
                                <input name="name" type="text" id="job-keyword" class="form-input w-full filter-input-box bg-gray-50 dark:bg-slate-800 border-0 focus:ring-transparent" placeholder="Search your keaywords">
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