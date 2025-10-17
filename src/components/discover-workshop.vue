<template>
    <div>
        <div v-if="discover" class="container md:mt-24 mt-16">
         
        </div>
    
        <div v-else-if="items" class="grid xl:grid-cols-4 lg:grid-cols-2 md:grid-cols-2 grid-cols-1 gap-[30px]">

        </div>

        <div v-else-if="explore" class="grid lg:grid-cols-2 grid-cols-1 gap-[30px]">
            <div v-for="product in setProductData" :key="product.id"  class="group relative p-2 rounded-lg bg-white dark:bg-slate-900 border border-gray-100 dark:border-gray-800 hover:shadow-md dark:shadow-md hover:dark:shadow-gray-700 transition-all duration-500 h-fit">
                <div class="absolute inset-0 bg-gradient-to-r from-red-600 to-violet-600 rounded-lg -mt-1 group-hover:-mt-2 -ms-1 group-hover:-ms-2 h-[98%] w-[98%] -z-1 transition-all duration-500"></div>
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

                    <div  v-if="product.showdate === true"
                    class="absolute bottom-2 start-0 end-0 mx-auto text-center bg-gradient-to-r from-violet-600 to-red-600 text-white inline-table text-lg px-3 rounded-full">
                        <i class="uil uil-clock align-middle me-1"></i> <small id="auction-item-1" class="font-bold">{{product.remaining?.days + " : " + product.remaining?.hours + " : " + product.remaining?.minutes + " : " + product.remaining?.seconds }}</small>
                    </div>
                </div>

                <div class="mt-3">
                    <!-- <div class="flex items-center">
                        <img :src="product.image" class="rounded-full size-8" alt="">
                        <router-link to="/creator-profile" class="ms-2 text-[15px] font-medium text-slate-400 hover:text-violet-600">{{ product.name}}</routerlink>
                    </div> -->

                    <div class="my-3 text-center">
                        <router-link :to="{name: 'details-workshop', params: {id: product.id}}" class="font-semibold hover:text-violet-600">{{ product.name }}</router-link>
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
                            <span v-for="(skill, idx) in product.skills" :key="idx" class="px-2 py-0.5 rounded-full bg-violet-600 text-white text-xs font-medium border border-violet-200">
                                {{ skill }}
                            </span>
                        </div>
                    </div>

                    <div class="flex justify-center items-center p-2 bg-violet-50 dark:bg-slate-800 rounded-lg shadow dark:shadow-gray-700">
                        <router-link :to="{name: 'details-workshop', params: {id: product.id}}" class=" px-6 text-black text-base font-semibold transition">Lihat Profil</router-link>
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
                        <router-link :to="{name: 'details-workshop', params: {id: product.id}}" class="btn btn-sm rounded-full bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white"><i class="mdi mdi-lightning-bolt"></i> Buy Now</router-link>
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
                        <router-link :to="{name: 'details-workshop', params: {id: product.id}}" class="font-semibold hover:text-violet-600">{{ product.name }}</router-link>
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
                            <span v-for="(skill, idx) in product.skills" :key="idx" class="px-2 py-0.5 rounded-full bg-violet-100 text-violet-700 text-xs font-medium border border-violet-200">
                                {{ skill }}
                            </span>
                        </div>
                        <router-link :to="{name: 'details-workshop', params: {id: product.id}}" class="inline-block mt-3 px-4 py-1 rounded-full bg-violet-600 hover:bg-violet-700 text-white text-xs font-semibold shadow transition">Lihat Profil</router-link>
                    </div>

                    <div class="flex justify-center items-center p-2 bg-gray-50 dark:bg-slate-800 rounded-lg shadow dark:shadow-gray-700">
                        <router-link :to="{name: 'details-workshop', params: {id: product.id}}" class="inline-block px-6 py-2 rounded-full bg-violet-600 hover:bg-violet-700 text-white text-base font-semibold shadow transition">Lihat Profil</router-link>
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
import { useWorkshopStore } from '@/stores/storeWorkshop.ts'


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
        setProductData: [],
        products: [
            {
                id: 1,
                mainimage: require('../assets/images/items/1.jpg'),
                image: require('../assets/images/avatar/1.jpg'),
                name: '@StreetBoy',
                title: 'Gensadsaduine Undjkbjbead #3902',
                location: 'Jakarta',
                rating: 5,
                skills: ['Desain Grafis', 'Fotografi'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
            {
                id: 2,
                mainimage: require('../assets/images/items/2.gif'),
                image: require('../assets/images/avatar/2.jpg'),
                name: '@CutieGirl',
                title: 'Windchime #768',
                location: 'Surabaya',
                rating: 4,
                skills: ['Web Development', 'UI/UX'],
                price: '3.5 ETH',
                date: 'August 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: true
            },
            {
                id: 3,
                mainimage: require('../assets/images/items/2.jpg'),
                image: require('../assets/images/items/3.gif'),
                name: '@ButterFly',
                title: 'Probably A Label #3277',
                location: 'Bandung',
                rating: 3,
                skills: ['Animasi', 'Ilustrasi'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
            {
                id: 4,
                mainimage: require('../assets/images/items/3.jpg'),
                image: require('../assets/images/avatar/3.jpg'),
                name: '@NorseQueen',
                title: 'Probably A Label #1711',
                location: 'Medan',
                rating: 5,
                skills: ['Digital Marketing', 'SEO'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
            {
                id: 5,
                mainimage: require('../assets/images/items/3.gif'),
                image: require('../assets/images/avatar/4.jpg'),
                name: '@BigBull',
                title: 'Shibuya Scramble Punks',
                location: 'Makassar',
                rating: 4,
                skills: ['Copywriting', 'Branding'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
            {
                id: 6,
                mainimage: require('../assets/images/items/4.jpg'),
                image: require('../assets/images/avatar/5.jpg'),
                name: '@Angel',
                title: 'Probably A Label #650',
                location: 'Yogyakarta',
                rating: 3,
                skills: ['Video Editing', 'Motion Graphic'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
            {
                id: 7,
                mainimage: require('../assets/images/items/5.jpg'),
                image: require('../assets/images/avatar/6.jpg'),
                name: '@CrazyAnyone',
                title: 'Looki#0147',
                location: 'Semarang',
                rating: 5,
                skills: ['Mobile App', 'UI/UX'],
                price: '3.5 ETH',
                date: 'January 29, 2026 6:0:0',
                highest: '3.55 ETH',
                showdate: true
            },
            {
                id: 8,
                mainimage: require('../assets/images/items/6.jpg'),
                image: require('../assets/images/items/5.gif'),
                name: '@Princess',
                title: 'Poob #285',
                location: 'Denpasar',
                rating: 4,
                skills: ['Desain Logo', 'Branding'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
            {
                id: 9,
                mainimage: require('../assets/images/items/8.jpg'),
                image: require('../assets/images/avatar/7.jpg'),
                name: '@LooserBad',
                title: 'Umber Arrow',
                location: 'Palembang',
                rating: 3,
                skills: ['Ilustrasi', 'Desain Grafis'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
            {
                id: 10,
                mainimage: require('../assets/images/items/4.gif'),
                image: require('../assets/images/items/5.gif'),
                name: '@Princess',
                title: 'Gloam Druid',
                location: 'Balikpapan',
                rating: 4,
                skills: ['Web Development', 'SEO'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
            {
                id: 11,
                mainimage: require('../assets/images/items/5.gif'),
                image: require('../assets/images/avatar/8.jpg'),
                name: '@PandaOne',
                title: 'Azuki #7421',
                location: 'Pontianak',
                rating: 5,
                skills: ['Animasi', 'Video Editing'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
            {
                id: 12,
                mainimage: require('../assets/images/items/9.jpg'),
                image: require('../assets/images/items/2.gif'),
                name: '@FunnyGuy',
                title: 'Wolf-Cult Vanguard',
                location: 'Padang',
                rating: 3,
                skills: ['Branding', 'Copywriting'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
        ]
    }
},

mounted() {
    const workshopStore = useWorkshopStore()
    workshopStore.getWorkshop().then(() => {
        this.setProductData = workshopStore.workshops.map(item => ({
            ...item,
            remaining: this.tickTock(item.date),
        }))
    })

    this._interval = setInterval(() => {
        const workshopStore = useWorkshopStore()
        this.setProductData = workshopStore.workshops.map(item => ({
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
    // remainingDays tidak perlu lagi, karena sudah dihandle di mounted & interval
}
}
</script>

<style lang="scss" scoped></style>