<template>
    <div>
        <div v-if="explore" class="grid lg:grid-cols-1 grid-cols-1 gap-[30px]">
            <div v-for="product in setProductData" :key="product.id"  class="group relative p-2 rounded-lg bg-white dark:bg-slate-900 border border-gray-100 dark:border-gray-800 hover:shadow-md dark:shadow-md hover:dark:shadow-gray-700 transition-all duration-500 h-fit">
                <div class="absolute inset-0 bg-gradient-to-r from-red-600 to-violet-600 rounded-lg -mt-1 group-hover:-mt-2 -ms-1 group-hover:-ms-2 h-[98%] w-[98%] -z-1 transition-all duration-500"></div>
                <div class="relative overflow-hidden">
                    <div class="relative overflow-hidden flex flex-col md:flex-row items-center md:items-start p-4 gap-6">
                        <div class="relative flex-shrink-0 flex items-center justify-center w-full md:w-48">
                            <img :src="product.image_url" class="rounded-lg shadow-md dark:shadow-gray-700 group-hover:scale-105 transition-all duration-500 object-cover w-40 h-40 md:w-48 md:h-48 bg-gray-100" alt="">
                            <div v-if="product.showdate === true" class="absolute bottom-2 left-1/2 -translate-x-1/2 text-center bg-gradient-to-r from-violet-600 to-red-600 text-white inline-table text-lg px-3 rounded-full">
                                <i class="uil uil-clock align-middle me-1"></i> <small class="font-bold">{{product.remaining?.days + " : " + product.remaining?.hours + " : " + product.remaining?.minutes + " : " + product.remaining?.seconds }}</small>
                            </div>
                        </div>
                        <div class="flex-1 w-full">
                            <div class="flex flex-col md:flex-row md:items-center md:justify-between">
                                <div>
                                    <router-link :to="{name: 'details-technician', params: {id: product.id}}" class="font-semibold text-2xl hover:text-violet-600">{{ product.display_name }}</router-link>
                                    <div class="text-xs text-slate-400 mt-1 flex items-center gap-1">
                                        <i class="mdi mdi-map-marker"></i> {{ product.location }}
                                    </div>
                                    <div class="flex items-center mt-1">
                                        <span v-for="n in 5" :key="n">
                                            <i v-if="n <= (product.rating || 0)" class="mdi mdi-star text-yellow-400"></i>
                                            <i v-else class="mdi mdi-star-outline text-yellow-400"></i>
                                        </span>
                                    </div>
                                    <div v-if="product.skills && product.skills.length" class="flex flex-wrap items-center gap-2 mt-2">
                                        <span
                                          v-for="(skill, idx) in (Array.isArray(product.skills) ? product.skills : product.skills.split(','))"
                                          :key="idx"
                                          class="px-2 py-0.5 rounded-full bg-violet-100 text-violet-700 text-xs font-medium border border-violet-200"
                                        >
                                          {{ skill.trim() }}
                                        </span>
                                    </div>
                                    <div class="mt-2 text-sm text-slate-600 dark:text-slate-300">
                                        {{ product.short_description }}
                                    </div>
                                </div>
                            </div>
                            <div class="flex flex-wrap gap-3 mt-4">
                                <router-link :to="{name: 'details-technician', params: {id: product.id}}" class="btn btn-sm rounded-full bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white flex items-center"><i class="mdi mdi-lightning-bolt mr-1"></i> Hubungi</router-link>
                                <router-link :to="{name: 'details-technician', params: {id: product.id}}" class="btn btn-sm rounded-full bg-gray-200 dark:bg-slate-800 text-violet-700 dark:text-white border border-violet-200 dark:border-slate-700 hover:bg-violet-600 hover:text-white hover:border-violet-600 transition">Lihat Profil</router-link>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        

        <div v-else class="grid xl:grid-cols-4 lg:grid-cols-3 md:grid-cols-2 grid-cols-1 mt-10 gap-[30px]">
            <div v-for="product in setProductData.slice(0, 8)" :key="product.id" class="group relative overflow-hidden p-2 rounded-lg bg-white dark:bg-slate-900 border border-gray-100 dark:border-gray-800 hover:shadow-md dark:shadow-md hover:dark:shadow-gray-700 transition-all duration-500 hover:-mt-2 h-fit">
                <div class="relative overflow-hidden">
                    <div class="relative overflow-hidden rounded-lg">
                        <img :src="product.image_url" class="mt-6 rounded-lg shadow-md dark:shadow-gray-700 group-hover:scale-110 transition-all duration-500 object-cover w-40 h-40 md:w-48 md:h-48 mx-auto bg-gray-100" alt="">
                    </div>

                    <div class="absolute -bottom-20 group-hover:bottom-1/2 group-hover:translate-y-1/2 start-0 end-0 mx-auto text-center transition-all duration-500">
                        <router-link :to="{name: 'item-detail', params: {id: product.id}}" class="btn btn-sm rounded-full bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white"><i class="mdi mdi-lightning-bolt"></i> Buy Now</router-link>
                    </div>

                    <div class="absolute top-2 end-2 opacity-0 group-hover:opacity-100 transition-all duration-500">
                        <a href="javascript:void(0)" class="btn btn-icon btn-sm rounded-full bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white"><i class="mdi mdi-plus"></i></a>
                    </div>

                    <div v-if="product.showdate === true" class="absolute  bottom-2 start-0 end-0 mx-auto text-center bg-gradient-to-r from-violet-600 to-red-600 text-white inline-table text-lg px-3 rounded-full justify-center">
                        <i class="uil uil-clock align-middle me-1 text-center"></i>  <small id="auction-item-1" class="font-bold"> {{ product.remaining?.days + " : " + product.remaining?.hours + " : " + product.remaining?.minutes + " : " + product.remaining?.seconds }}</small>
                    </div>
                </div>

                <div class="mt-3">
                    <!-- <div class="flex items-center">
                        <img :src="product.image" class="rounded-full size-8" alt="">
                        <router-link to="/creator-profile" class="ms-2 text-[15px] font-medium text-slate-400 hover:text-violet-600">{{ product.name}}</routerlink>
                    </div> -->

                    <div class="my-3 text-center">
                        <router-link :to="{name: 'details-technician', params: {id: product.id}}" class="font-semibold hover:text-violet-600">{{ product.display_name }}</router-link>
                        <div class="text-xs text-slate-400 mt-1 flex items-center justify-center gap-1">
                            <i class="mdi mdi-map-marker"></i> {{ product.location }}
                        </div>
                        <div class="flex items-center justify-center mt-1">
                            <span v-for="n in 5" :key="n">
                                <i v-if="n <= (product.rating || 0)" class="mdi mdi-star text-yellow-400"></i>
                                <i v-else class="mdi mdi-star-outline text-yellow-400"></i>
                            </span>
                        </div>
                        <div v-if="product.skills && product.skills.length" class="flex flex-wrap items-center justify-center gap-2 mt-2">
                            <span
                              v-for="(skill, idx) in (Array.isArray(product.skills) ? product.skills : product.skills.split(','))"
                              :key="idx"
                              class="px-2 py-0.5 rounded-full bg-violet-100 text-violet-700 text-xs font-medium border border-violet-200"
                            >
                              {{ skill.trim() }}
                            </span>
                        </div>
                        <div class="mt-2 text-sm text-slate-600 dark:text-slate-300">
                            {{ product.short_description }}
                        </div>
                        <router-link :to="{name: 'details-technician', params: {id: product.id}}" class="inline-block mt-3 px-4 py-1 rounded-full bg-violet-600 hover:bg-violet-700 text-white text-xs font-semibold shadow transition">Lihat Profil</router-link>
                    </div>

                    <div class="flex justify-center items-center p-2 bg-gray-50 dark:bg-slate-800 rounded-lg shadow dark:shadow-gray-700">
                        <router-link :to="{name: 'details-technician', params: {id: product.id}}" class="inline-block px-6 py-2 rounded-full bg-violet-600 hover:bg-violet-700 text-white text-base font-semibold shadow transition">Lihat Profil</router-link>
                    </div>
                </div>
            </div><!--end content-->
        </div>

        <div v-if="moreitem" class="grid grid-cols-1 mt-6">
            <div class="text-center">
                <router-link to="/explore-one" class="btn btn-link text-[16px] font-medium hover:text-violet-600 after:bg-violet-600 duration-500 ease-in-out">Explore More <i class="uil uil-arrow-right"></i></router-link>
            </div>
        </div>
    </div>
</template>

<script>
import { useTechnicianStore } from '@/stores/storeTechnician'

export default {
    props: {
        discover: { type: Boolean, required: true },
        items: { type: Boolean, required: true },
        moreitem: { type: Boolean, required: true },
        explore: { type: Boolean, required: true },
    },
    name: "DiscoverTeknisi",
    data() {
        return {
            setProductData: [],
        }
    },
    mounted() {
        const technicianStore = useTechnicianStore()
        technicianStore.getTechnicians().then(() => {
            this.setProductData = technicianStore.technicians.map(item => ({
                ...item,
                remaining: this.tickTock(item.date),
            }))
        })

        this._interval = setInterval(() => {
            const technicianStore = useTechnicianStore()
            this.setProductData = technicianStore.technicians.map(item => ({
                ...item,
                remaining: this.tickTock(item.date),
            }))
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
    }
}
</script>

<style lang="scss" scoped></style>