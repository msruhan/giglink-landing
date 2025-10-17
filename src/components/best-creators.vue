<template>
    <div class="grid lg:grid-cols-3 md:grid-cols-2 grid-cols-1 mt-10 gap-[30px]">

        <div v-for="item in datas" :key="item" class="flex justify-between items-center p-3 rounded-md bg-white dark:bg-slate-900 shadow dark:shadow-gray-800">
            <div class="flex items-center">
                <div class="relative inline-block">
                    <img :src="item.image_url" class="h-16 rounded-md" alt="">
                    <i class="mdi mdi-check-decagram text-emerald-600 text-lg absolute -top-2 -end-2"></i>
                </div>

                <div class="ms-3">
                     <router-link :to="{name: 'details-technician', params: {id: item.id}}" class="font-semibold block hover:text-violet-600">{{item.display_name}}</router-link>
                    <span class="text-slate-400 text-sm block mt-0.5">{{ item.title }}</span>
                </div>
            </div>

            <router-link :to="{name: 'details-technician', params: {id: item.id}}" class="btn btn-icon rounded-full bg-violet-600/5 hover:bg-violet-600 border-violet-600/10 hover:border-violet-600 text-violet-600 hover:text-white">
                <i class="uil uil-search text-[20px]"></i>
            </router-link>
        </div>
        <!--end content-->
        <!--end content-->
    </div><!--end grid-->
           

</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useTechnicianStore } from '@/stores/storeTechnician'

const technicianStore = useTechnicianStore()
const datas = ref([])

onMounted(async () => {
  await technicianStore.getTechnicians()
  datas.value = [...technicianStore.technicians]
    .sort((a, b) => (b.rating || 0) - (a.rating || 0))
    .slice(0, 9)
})
</script>

<style lang="scss" scoped>

</style>