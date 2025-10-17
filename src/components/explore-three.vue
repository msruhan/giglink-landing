<template>
            <div>
                <div class="grid grid-cols-1 items-center gap-[30px]">
                    <div class="filters-group-wrap text-center">
                        <div class="filters-group">
                            <ul class="mb-0 list-none container-filter-box filter-options">
                                <li class="inline-block font-medium text-base mx-1.5 mb-3 py-1 px-3 cursor-pointer relative text-slate-400 border border-gray-100 dark:border-gray-700 rounded-full transition duration-500"  :class="selectedCategory == null ? 'active' : ''" @click="matchCategory(null)"><i class="uil uil-browser"></i>  All</li>
                                <li class="inline-block font-medium text-base mx-1.5 mb-3 py-1 px-3 cursor-pointer relative text-slate-400 border border-gray-100 dark:border-gray-700 rounded-full transition duration-500" :class="selectedCategory == 'games' ? 'active' : ''" @click="matchCategory('games')"><i class="uil uil-volleyball"></i> Games</li>
                                <li class="inline-block font-medium text-base mx-1.5 mb-3 py-1 px-3 cursor-pointer relative text-slate-400 border border-gray-100 dark:border-gray-700 rounded-full transition duration-500" :class="selectedCategory == 'art' ? 'active' : ''" @click="matchCategory('art')"><i class="uil uil-chart-pie-alt"></i> Art</li>
                                <li class="inline-block font-medium text-base mx-1.5 mb-3 py-1 px-3 cursor-pointer relative text-slate-400 border border-gray-100 dark:border-gray-700 rounded-full transition duration-500" :class="selectedCategory == 'music' ? 'active' : ''" @click="matchCategory('music')"><i class="uil uil-music"></i> Music</li>
                                <li class="inline-block font-medium text-base mx-1.5 mb-3 py-1 px-3 cursor-pointer relative text-slate-400 border border-gray-100 dark:border-gray-700 rounded-full transition duration-500" :class="selectedCategory == 'video' ? 'active' : ''" @click="matchCategory('video')"><i class="uil uil-camera-plus"></i> Video</li>
                                <li class="inline-block font-medium text-base mx-1.5 mb-3 py-1 px-3 cursor-pointer relative text-slate-400 border border-gray-100 dark:border-gray-700 rounded-full transition duration-500" :class="selectedCategory == 'memes' ? 'active' : ''" @click="matchCategory('memes')"><i class="uil uil-rocket"></i> Memes</li>
                            </ul>
                        </div>
                    </div>
                </div><!--grid-->

                <div id="grid" class="lg:columns-4 md:columns-2 columns-2 mx-3 gap-6 mt-5">
                    <div v-for="product in filteredData" :key="product.id" class="picture-item mb-6" data-groups='["games"]'>
                        <div class="group relative overflow-hidden p-2 rounded-lg bg-white dark:bg-slate-900 border border-gray-100 dark:border-gray-800 hover:shadow-md dark:shadow-md hover:dark:shadow-gray-700 transition-all duration-500 hover:-mt-2 h-fit">
                            <div class="relative overflow-hidden">
                                <div class="relative overflow-hidden rounded-lg">
                                    <img :src="product.mainimage" class="rounded-lg shadow-md dark:shadow-gray-700 group-hover:scale-110 transition-all duration-500" alt="">
                                </div>

                                <div class="absolute -bottom-20 group-hover:bottom-1/2 group-hover:translate-y-1/2 start-0 end-0 mx-auto text-center transition-all duration-500">
                                    <router-link :to="{name: 'item-detail', params: {id: product.id}}" class="btn btn-sm rounded-full bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white"><i class="mdi mdi-lightning-bolt"></i> Buy Now</router-link>                                
                                </div>

                                <div class="absolute top-2 end-2 opacity-0 group-hover:opacity-100 transition-all duration-500">
                                    <a href="javascript:void(0)" class="btn btn-icon btn-sm rounded-full bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white"><i class="mdi mdi-plus"></i></a>
                                </div>

                                <div  v-if="product.showdate === true" class="absolute bottom-2 start-0 end-0 mx-auto text-center bg-gradient-to-r from-violet-600 to-red-600 text-white inline-table text-lg px-3 rounded-full">
                                    <i class="uil uil-clock align-middle me-1"></i> <small id="auction-item-1" class="font-bold">{{ product.remaining?.days + " : " + product.remaining?.hours + " : " + product.remaining?.minutes + " : " + product.remaining?.seconds }}</small>
                                </div>
                            </div>

                            <div class="mt-3">
                                <div class="flex items-center">
                                    <img :src="product.image" class="rounded-full size-8" alt="">
                                    <router-link to="/creator-profile" class="ms-2 text-[15px] font-medium text-slate-400 hover:text-violet-600">{{product.name}}</router-link>
                                </div>

                                <div class="my-3">
                                    <router-link :to="{name: 'item-detail', params: {id: product.id}}" class="font-semibold hover:text-violet-600">{{product.title}}</router-link>
                                </div>

                                <div class="flex justify-between p-2 bg-gray-50 dark:bg-slate-800 rounded-lg shadow dark:shadow-gray-700">
                                    <div>
                                        <span class="text-[16px] font-medium text-slate-400 block">Price</span>
                                        <span class="text-[16px] font-semibold block"><i class="mdi mdi-ethereum"></i> {{product.price}}</span>
                                    </div>
                                    
                                    <div>
                                        <span class="text-[16px] font-medium text-slate-400 block">Highest Bid</span>
                                        <span class="text-[16px] font-semibold block"><i class="mdi mdi-ethereum"></i> {{product.highest}}</span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div><!--end content-->
                </div><!--end grid-->
            </div>
</template>

<script>

export default {
    data() {
        return {
            products: [
                {
                    id: 1,
                    mainimage: require('../assets/images/items/1.jpg'),
                    image: require('../assets/images/avatar/1.jpg'),
                    name: '@StreetBoy',
                    title: 'Genuine Undead #3902',
                    price: '3.5 ETH',
                    highest: '3.55 ETH',
                    category: 'games',
                    date: 'January 29, 2025 6:0:0',
                    showdate: false
                },
                {
                    id: 2,
                    mainimage: require('../assets/images/items/3.gif'),
                    image: require('../assets/images/avatar/4.jpg'),
                    name: '@BigBull',
                    title: 'Shibuya Scramble Punks',
                    price: '3.5 ETH',
                    highest: '3.55 ETH',
                    category: 'memes',
                    date: 'January 29, 2025 6:0:0',
                    showdate: false
                },
                {
                    id: 3,
                    mainimage: require('../assets/images/items/8.jpg'),
                    image: require('../assets/images/avatar/7.jpg'),
                    name: '@LooserBad',
                    title: 'Umber Arrow',
                    price: '3.5 ETH',
                    highest: '3.55 ETH',
                    category: 'video',
                    date: 'January 29, 2025 6:0:0',
                    showdate: false
                },
                {
                    id: 4,
                    mainimage: require('../assets/images/items/2.gif'),
                    image: require('../assets/images/avatar/2.jpg'),
                    name: '@CutieGirl',
                    title: 'Windchime #768',
                    price: '3.5 ETH',
                    highest: '3.55 ETH',
                    category: 'art',
                    date: 'January 29, 2025 6:0:0',
                    showdate: true
                },
                {
                    id: 5,
                    mainimage: require('../assets/images/items/4.jpg'),
                    image: require('../assets/images/avatar/5.jpg'),
                    name: '@Angel',
                    title: 'Probably A Label #650',
                    price: '3.5 ETH',
                    highest: '3.55 ETH',
                    category: 'games',
                    date: 'January 29, 2025 6:0:0',
                    showdate: false
                },
                {
                    id: 6,
                    mainimage: require('../assets/images/items/4.gif'),
                    image: require('../assets/images/items/5.gif'),
                    name: '@Princess',
                    title: 'Gloam Druid',
                    price: '3.5 ETH',
                    highest: '3.55 ETH',
                    category: 'art',
                    date: 'January 29, 2025 6:0:0',
                    showdate: false
                },
                {
                    id: 7,
                    mainimage: require('../assets/images/items/2.jpg'),
                    image: require('../assets/images/items/3.gif'),
                    name: '@ButterFly',
                    title: 'Probably A Label #3277',
                    price: '3.5 ETH',
                    highest: '3.55 ETH',
                    category: 'music',
                    date: 'January 29, 2025 6:0:0',
                    showdate: false
                },
                {
                    id: 8,
                    mainimage: require('../assets/images/items/5.jpg'),
                    image: require('../assets/images/avatar/6.jpg'),
                    name: '@CrazyAnyone',
                    title: 'Looki#0147',
                    price: '3.5 ETH',
                    highest: '3.55 ETH',
                    category: 'art',
                    date: 'January 29, 2025 6:0:0',
                    showdate: true
                },
                {
                    id: 9,
                    mainimage: require('../assets/images/items/5.gif'),
                    image: require('../assets/images/avatar/8.jpg'),
                    name: '@PandaOne',
                    title: 'Azuki #7421',
                    price: '3.5 ETH',
                    highest: '3.55 ETH',
                    category: 'games',
                    date: 'January 29, 2025 6:0:0',
                    showdate: false
                },
                {
                    id: 10,
                    mainimage: require('../assets/images/items/3.jpg'),
                    image: require('../assets/images/avatar/3.jpg'),
                    name: '@NorseQueen',
                    title: 'Probably A Label #1711',
                    price: '3.5 ETH',
                    highest: '3.55 ETH',
                    category: 'video',
                    date: 'January 29, 2025 6:0:0',
                    showdate: false
                },
                {
                    id: 11,
                    mainimage: require('../assets/images/items/6.jpg'),
                    image: require('../assets/images/items/5.gif'),
                    name: '@Princess',
                    title: 'Poob #285',
                    price: '3.5 ETH',
                    highest: '3.55 ETH',
                    category: 'music',
                    date: 'January 29, 2025 6:0:0',
                    showdate: false
                },
                {
                    id: 12,
                    mainimage: require('../assets/images/items/9.jpg'),
                    image: require('../assets/images/items/2.gif'),
                    name: '@FunnyGuy',
                    title: 'Wolf-Cult Vanguard',
                    price: '3.5 ETH',
                    highest: '3.55 ETH',
                    category: 'music',
                    date: 'January 29, 2025 6:0:0',
                    showdate: false
                },
            ],
            productData: [],
            selectedCategory: null,
            filteredData: []
        }
    },
    created() {
        this.productData = this.products;
    },
    mounted() {
        this.interval = setTimeout(() => {
            this.remainingDays();
            this.matchCategory()
        }, );
        return () => clearInterval(this.interval);
    },

    methods: {
        remainingDays() {
            const formattedData = this.products.map((item) => ({
                ...item,
                remaining: this.tickTock(item.date),

            }));
            this.productData = formattedData;
        },
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
        matchCategory(category) {
            this.selectedCategory = category
            this.filteredData = this.selectedCategory ? this.productData.filter((item) => item.category === this.selectedCategory)
                : this.productData;
                
        },

},

}

</script>

<style lang="scss" scoped>

</style>