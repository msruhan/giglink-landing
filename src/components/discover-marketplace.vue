<template>
    <div>
        <div v-if="discover" class="container md:mt-24 mt-16">

        </div><!--end container-->
    
        <div v-else class="grid xl:grid-cols-4 lg:grid-cols-3 md:grid-cols-2 grid-cols-1 mt-10 gap-[30px]">
            <div v-for="product in setProductData.slice(0, 8)" :key="product.id" class="group relative overflow-hidden p-2 rounded-lg bg-white dark:bg-slate-900 border border-gray-100 dark:border-gray-800 hover:shadow-md dark:shadow-md hover:dark:shadow-gray-700 transition-all duration-500 hover:-mt-2 h-fit flex flex-col justify-between min-h-[410px]">
                <div class="flex-1 flex flex-col justify-between">
                    <div>
                        <div class="relative overflow-hidden rounded-lg">
                            <img :src="product.image_url_1" class="rounded-lg shadow-md dark:shadow-gray-700 group-hover:scale-110 transition-all duration-500" alt="">
                        </div>
                        <div class="absolute -bottom-20 group-hover:bottom-1/2 group-hover:translate-y-1/2 start-0 end-0 mx-auto text-center transition-all duration-500">
                            <router-link :to="{name: 'item-detail', params: {id: product.id}}" class="btn btn-sm rounded-full bg-violet-600 bg-opacity-80 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white mr-2 min-w-[100px] flex justify-center items-center"><i class="mdi mdi-eye"></i> Lihat Detail</router-link>
                            <router-link :to="{name: 'creator-chat', params: {id: product.id}}" class="btn btn-sm rounded-full bg-green-600 bg-opacity-80 hover:bg-green-700 border-green-600 hover:border-green-700 text-white min-w-[100px] flex justify-center items-center"><i class="mdi mdi-chat"></i> Chat Penjual</router-link>
                        </div>
                        <div class="absolute top-2 end-2 opacity-0 group-hover:opacity-100 transition-all duration-500">
                            <a href="javascript:void(0)" class="btn btn-icon btn-sm rounded-full bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white"><i class="mdi mdi-plus"></i></a>
                        </div>
                        <div v-if="product.showdate === true" class="absolute bottom-6 start-0 end-0 mx-auto text-center bg-gradient-to-r from-violet-600 to-red-600 text-white inline-table text-lg px-3 rounded-full justify-center z-10">
                            <i class="uil uil-clock align-middle me-1 text-center"></i>  <small id="auction-item-1" class="font-bold"> {{ product.remaining?.days + " : " + product.remaining?.hours + " : " + product.remaining?.minutes + " : " + product.remaining?.seconds }}</small>
                        </div>
                    </div>
                    <div class="mt-3">
                        <div class="my-3 flex items-center gap-3">
                            <div>
                                <div class="font-semibold text-lg hover:text-violet-600 line-clamp-2 min-h-[48px]">{{ product.title }}</div>
                                <div class="flex items-center gap-2 text-xs text-slate-400 mt-1">
                                    <i class="mdi mdi-eye"></i> {{ product.views || 0 }}x dilihat
                                    <span class="ml-3 flex items-center"><i class="mdi mdi-star text-yellow-400"></i> {{ product.rating || 0 }}/5</span>
                                    <span v-if="product.type"
                                          :class="[
                                            'ml-3 inline-block px-2 py-0.5 rounded-full text-xs font-semibold border',
                                            product.type === 'New'
                                              ? 'bg-green-100 text-green-700 border-green-300'
                                              : product.type === 'Second'
                                                ? 'bg-yellow-100 text-yellow-700 border-yellow-300'
                                                : 'bg-gray-100 text-gray-700 border-gray-300'
                                          ]">
                                        {{ product.type }}
                                    </span>
                                </div>
                                    <span v-if="product.posting" class="text-xs text-slate-400 italic">{{ product.posting }}</span>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="flex justify-between items-center p-2 bg-gray-50 dark:bg-slate-800 rounded-lg shadow dark:shadow-gray-700 mt-1">
                    <span class="text-[16px] font-medium text-slate-400">Harga</span>
                    <span class="text-[18px] font-bold text-violet-700 flex items-center"><i class="mdi mdi-cash mr-1"></i>{{ formatRupiah(product.price) }}</span>
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
import { useProductStore } from '@/stores/storeProduct'
export default {
    props: {
        discover: { type: Boolean, required: true },
        items: { type: Boolean, required: true },
        moreitem: { type: Boolean, required: true },
        explore: { type: Boolean, required: true },
    },
    name: "ExploreOne",
    data() {
        return {
            setProductData: [],
        }
    },
    mounted() {
        const productStore = useProductStore()
        productStore.getProducts().then(() => {
            this.setProductData = productStore.products.map(item => ({
                ...item,
                remaining: this.tickTock(item.date),
            }))
        })

        this._interval = setInterval(() => {
            const productStore = useProductStore()
            this.setProductData = productStore.products.map(item => ({
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
        formatRupiah(value) {
            if (!value) return 'Rp0';
            return 'Rp' + value.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
        },
    }
}
</script>

<style lang="scss" scoped></style>