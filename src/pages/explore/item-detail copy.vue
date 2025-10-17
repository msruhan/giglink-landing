<template>
    <div>
        <navbar />
        <!-- Start -->
        <section class="relative pt-28 md:pb-24 pb-16">
            <div class="container">
                <div class="grid lg:grid-cols-12 md:grid-cols-2 grid-cols-1 gap-[30px]">
                    <div class="lg:col-span-5">
                        <img :src="data?.mainimage ? data?.mainimage : image" class="rounded-md shadow dark:shadow-gray-700" alt="">

                        <div class="bg-gray-50 dark:bg-slate-800 rounded-md shadow dark:shadow-gray-800 mt-[30px] p-6">
                            <div>
                                <span class="font-medium text-slate-400 block mb-1">Contract Address</span>
                                <a href="" class="font-medium text-violet-600 underline block">1fsvtgju51ntgeryimghf6ty7o9n3r3er246</a>
                            </div>

                            <div class="mt-4">
                                <span class="font-medium text-slate-400 block mb-1">Token ID</span>
                                <span class="font-medium block">458342529342930944</span>
                            </div>

                            <div class="mt-4">
                                <span class="font-medium text-slate-400 block mb-1">Blockchain</span>
                                <span class="font-medium block">ETH</span>
                            </div>

                            <div class="mt-4">
                                <span class="font-medium text-slate-400 block mb-1">Deposit & Withdraw</span>
                                <span class="font-medium block">Unsupported</span>
                            </div>
                        </div>
                    </div><!--end col-->

                    <div class="lg:col-span-7 lg:ms-8">
                        <h5 class="md:text-2xl text-xl font-semibold">{{ data?.title ? data?.title : 'Probably A Label #3277'}}</h5>

                        <span class="font-medium text-slate-400 block mt-2">From this collection: <router-link to="/creator-profile" class="text-violet-600">{{ data?.name ? data?.name : '@FunnyGuy' }}</router-link></span>

                        <p class="text-slate-400 mt-4">Hey guys! New exploration about NFT Marketplace Web Design, this time I'm inspired by one of my favorite NFT website called Giglink (with crypto payment)! What do you think?</p>
                        <p class="text-slate-400 mt-4">What does it mean? Biomechanics is the study of the structure, function and motion of the mechanical aspects of biological systems, at any level from whole organisms to organs, cells and cell organelles, using the methods of mechanics. Biomechanics is a branch of biophysics.</p>

                        <div class="mt-4">
                            <span class="text-lg font-medium text-slate-400 block">Market Price</span>
                            <span class="tmd:text-2xl text-xl font-semibold block mt-2"><i class="mdi mdi-ethereum"></i> 3.5 ETH = $ 4,659.75</span>
                        </div>

                        <div class="mt-6">
                            <a @click="toggle" href="javascript:void(0)" class="btn rounded-full bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white me-1"><i class="mdi mdi-gavel"></i> Bid Now</a>
                            <a @click="toggle2" href="javascript:void(0)" class="btn rounded-full bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white"><i class="mdi mdi-lightning-bolt"></i> Buy Now</a>
                        </div>

                        <div class="md:flex p-6 bg-gray-50 dark:bg-slate-800 rounded-lg shadow dark:shadow-gray-700 mt-6">
                            <div class="md:w-1/2">
                                <div class="flex items-center">
                                    <div class="relative inline-block">
                                        <img :src="data?.image ? data?.image : image2" class="h-16 rounded-md" alt="">
                                        <i class="mdi mdi-check-decagram text-emerald-600 text-lg absolute -top-2 -end-2"></i>
                                    </div>

                                    <div class="ms-3">
                                        <router-link to="/creator-profile" class="font-semibold block hover:text-violet-600">Michael Williams</router-link>
                                        <span class="text-slate-400 text-[16px] block mt-1">Creator</span>
                                    </div>
                                </div>
                            </div>

                            <div class="md:w-1/2 md:mt-0 mt-4">
                                <div class="flex items-center">
                                    <div class="relative inline-block">
                                        <img src="../../assets/images/avatar/1.jpg" class="h-16 rounded-md" alt="">
                                        <i class="mdi mdi-check-decagram text-emerald-600 text-lg absolute -top-2 -end-2"></i>
                                    </div>

                                    <div class="ms-3">
                                        <router-link to="/creator-profile" class="font-semibold block hover:text-violet-600">Michael Williams</router-link>
                                        <span class="text-slate-400 text-[16px] block mt-1">Owner</span>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <div class="grid grid-cols-1 mt-8">
                            <ul class="md:w-fit w-full flex-wrap justify-center text-center p-3 bg-white dark:bg-slate-900 shadow dark:shadow-gray-800 rounded-md" id="myTab" data-tabs-toggle="#StarterContent" role="tablist">
                                <li role="presentation" class="md:inline-block block md:w-fit w-full me-1">
                                    <button @click="toggles(1)" :class="isActiveIndex === 1 ? 'text-white bg-violet-600' : 'dark:hover:bg-slate-800 hover:text-violet-600  hover:bg-gray-50 dark:hover:text-white'" class="px-6 py-2 font-semibold rounded-md w-full transition-all duration-500 ease-in-out" id="wednesday-tab" data-tabs-target="#wednesday" type="button" role="tab" aria-controls="wednesday" aria-selected="true">Bids</button>
                                </li>
                                <li role="presentation" class="md:inline-block block md:w-fit w-full">
                                    <button @click="toggles(2)" :class="isActiveIndex === 2 ? 'text-white bg-violet-600 ' : 'dark:hover:bg-slate-800 hover:text-violet-600  hover:bg-gray-50 dark:hover:text-white'" class="px-6 py-2 font-semibold rounded-md w-full transition-all duration-500 ease-in-out" id="thursday-tab" data-tabs-target="#thursday" type="button" role="tab" aria-controls="thursday" aria-selected="false">Activity</button>
                                </li>
                            </ul>

                            <div id="StarterContent" class="mt-6">
                                <div :class="isActiveIndex === 1 ? '' : 'hidden'" id="wednesday" role="tabpanel" aria-labelledby="wednesday-tab">
                                    <div class="grid grid-cols-1">
                                        <div class="flex items-center">
                                            <div class="relative inline-block">
                                                <img src="../../assets/images/items/2.gif" class="h-16 rounded-md" alt="">
                                                <i class="mdi mdi-check-decagram text-emerald-600 text-lg absolute -top-2 -end-2"></i>
                                            </div>

                                            <div class="ms-3">
                                                <h6 class="font-semibold">2 WETH <span class="text-slate-400">by</span> 
                                                    <a href="" class="hover:text-violet-600 duration-500 ease-in-out">0xe849fa28a...ea14</a>
                                                </h6>
                                                <span class="text-slate-400 text-[16px]">6 hours ago</span>
                                            </div>
                                        </div>

                                        <div class="flex items-center mt-4">
                                            <div class="relative inline-block">
                                                <img src="../../assets/images/items/1.jpg" class="h-16 rounded-md" alt="">
                                                <i class="mdi mdi-check-decagram text-emerald-600 text-lg absolute -top-2 -end-2"></i>
                                            </div>

                                            <div class="ms-3">
                                                <h6 class="font-semibold">0.001 WETH <span class="text-slate-400">by</span>
                                                    <a href="" class="hover:text-violet-600 duration-500 ease-in-out">VOTwear</a>
                                                </h6>
                                                <span class="text-slate-400 text-[16px]">6 hours ago</span>
                                            </div>
                                        </div>

                                        <div class="flex items-center mt-4">
                                            <div class="relative inline-block">
                                                <img src="../../assets/images/items/2.jpg" class="h-16 rounded-md" alt="">
                                                <i class="mdi mdi-check-decagram text-emerald-600 text-lg absolute -top-2 -end-2"></i>
                                            </div>

                                            <div class="ms-3">
                                                <h6 class="font-semibold">1.225 WETH <span class="text-slate-400">by</span>
                                                    <a href="" class="hover:text-violet-600 duration-500 ease-in-out">PandaOne</a>
                                                </h6>
                                                <span class="text-slate-400 text-[16px]">6 hours ago</span>
                                            </div>
                                        </div>
                                    </div>
                                </div>

                                <div :class="isActiveIndex === 2 ? '' : 'hidden'" id="thursday" role="tabpanel" aria-labelledby="thursday-tab">
                                    <div class="grid grid-cols-1">
                                        <div class="flex items-center">
                                            <div class="relative inline-block">
                                                <img src="../../assets/images/items/1.gif" class="h-20 rounded-md" alt="">
                                                <i class="mdi mdi-check-decagram text-emerald-600 text-lg absolute -top-2 -end-2"></i>
                                            </div>

                                            <span class="content ms-3">
                                                <a href="" class="hover:text-violet-600 font-semibold block">Digital Art Collection</a>
                                                <span class="text-slate-400 block text-[16px] mt-1">Started Following <a href="" class="font-semibold hover:text-violet-600">@Panda</a></span>
                                                <span class="text-slate-400 block text-[16px]">1 hours ago</span>
                                            </span>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div><!--end col-->
                </div><!--end grid-->
            </div><!--end container-->
        </section><!--end section-->
        <!-- End -->

        <!-- Start Modal -->
        <div id="NftBid" :class="isActive ? 'fixed' : 'hidden'" tabindex="-1" class="z-50  flex items-center justify-center overflow-hidden m-auto bg-gray-900 bg-opacity-50 dark:bg-opacity-80 inset-0">
            <div class="relative w-full h-auto max-w-md p-4">
                <div class="relative bg-white dark:bg-slate-900 rounded-lg shadow dark:shadow-gray-800">
                    <div class="flex justify-between items-center px-6 py-4 border-b border-gray-100 dark:border-gray-700">
                        <h5 class="text-xl font-semibold">Place a Bid</h5>
                        <button type="button" class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm p-1.5 ms-auto inline-flex items-center dark:hover:bg-gray-800 dark:hover:text-white" data-modal-toggle="NftBid">
                            <svg @click="toggle" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20"
                                xmlns="http://www.w3.org/2000/svg">
                                <path fill-rule="evenodd"
                                    d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
                                    clip-rule="evenodd"></path>
                            </svg>
                        </button>
                    </div>
                    <div class="p-6">
                        <form class="text-start">
                            <div class="grid grid-cols-1">
                                <div class="mb-4">
                                    <label class="font-semibold" for="number">Your Bid Price:</label>
                                    <input name="etherium" id="number" type="number" class="form-input w-full text-[15px] py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-violet-600 dark:border-gray-800 dark:focus:border-violet-600 focus:ring-0 mt-3" placeholder="00.00 ETH">
                                </div>

                                <div class="mb-4">
                                    <label class="font-semibold" for="number2">Enter Your QTY:</label>
                                    <input name="quantity" id="number2" type="number" class="form-input w-full text-[15px] py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-violet-600 dark:border-gray-800 dark:focus:border-violet-600 focus:ring-0 mt-3" placeholder="0">
                                    <span class="text-slate-400 text-sm"><span class="text-slate-900 dark:text-white mt-1">Note:</span> Max. Qty 5</span>
                                </div>
                            </div>
                        </form>

                        <div class="pt-4 border-t dark:border-t-gray-800">
                            <div class="flex justify-between">
                                <p class="font-semibold text-sm"> You must bid at least:</p>
                                <p class="text-sm text-violet-600 font-semibold"> 1.22 ETH </p>
                            </div>
                            <div class="flex justify-between mt-1">
                                <p class="font-semibold text-sm"> Service free:</p>
                                <p class="text-sm text-violet-600 font-semibold"> 0.05 ETH </p>
                            </div>
                            <div class="flex justify-between mt-1">
                                <p class="font-semibold text-sm"> Total bid amount:</p>
                                <p class="text-sm text-violet-600 font-semibold"> 1.27 ETH </p>
                            </div>
                        </div>

                        <div class="mt-4">
                            <a href="javascript:void(0)" data-modal-toggle="NftBid" class="btn rounded-full bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white w-full"><i class="mdi mdi-gavel"></i> Place a Bid</a>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div id="NftBuynow" :class="isActive2 ? 'fixed' : 'hidden'" tabindex="-1" class="z-50 overflow-hidden inset-0 m-auto flex justify-center items-center">
            <div class="relative w-full h-auto max-w-md p-4">
                <div class="relative bg-white dark:bg-slate-900 rounded-lg shadow dark:shadow-gray-800">
                    <div class="flex justify-between items-center px-6 py-4 border-b border-gray-100 dark:border-gray-700">
                        <h5 class="text-xl font-semibold">Checkout</h5>
                        <button type="button" class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm p-1.5 ms-auto inline-flex items-center dark:hover:bg-gray-800 dark:hover:text-white" data-modal-toggle="NftBuynow">
                            <svg @click="toggle2" class="size-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
                                <path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd"></path>
                            </svg>
                        </button>
                    </div>
                    <div class="p-6">
                        <form class="text-start">
                            <div class="grid grid-cols-1">
                                <div class="mb-4">
                                    <label class="font-semibold" for="number3">Your Price:</label>
                                    <input name="etherium" id="number3" type="number" class="form-input w-full text-[15px] py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-violet-600 dark:border-gray-800 dark:focus:border-violet-600 focus:ring-0 mt-3" placeholder="00.00 ETH">
                                </div>
                            </div>
                        </form>

                        <div class="pt-4 border-t dark:border-t-gray-800">
                            <div class="flex justify-between">
                                <p class="font-semibold text-sm"> You must bid at least:</p>
                                <p class="text-sm text-violet-600 font-semibold"> 1.22 ETH </p>
                            </div>
                            <div class="flex justify-between mt-1">
                                <p class="font-semibold text-sm"> Service free:</p>
                                <p class="text-sm text-violet-600 font-semibold"> 0.05 ETH </p>
                            </div>
                            <div class="flex justify-between mt-1">
                                <p class="font-semibold text-sm"> Total bid amount:</p>
                                <p class="text-sm text-violet-600 font-semibold"> 1.27 ETH </p>
                            </div>
                        </div>

                        <div class="flex items-center p-4 bg-red-600/10 text-red-600 mt-4 rounded-lg">
                            <i class="uil uil-exclamation-octagon text-3xl"></i>

                            <div class="ms-2">
                                <span class="block font-semibold">This creator is not verified</span>
                                <span class="block">Purchase this item at your own risk</span>
                            </div>
                        </div>

                        <div class="mt-4">
                            <a href="javascript:void(0)" data-modal-toggle="NftBuynow" class="btn rounded-full bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white w-full"><i class="mdi mdi-lightning-bolt"></i> Buy Now</a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <!-- End Modal -->

        <switcher />
        <footers />
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import navbar from '@/components/navbar/navbar.vue';
import switcher from '@/components/switcher.vue';
import footers from '@/components/footer/footer.vue'
import { useRoute } from 'vue-router';
import image from '../../assets/images/items/3.gif'
import image2 from '../../assets/images/avatar/1.jpg'

const route = useRoute();
const id = ref('')
const data = ref('')
const isActive = ref(false)
const isActive2 = ref(false)
const isActiveIndex = ref(1)


const datas = ref([
    {
        id: 1,
        mainimage: require('../../assets/images/items/1.jpg'),
        image: require('../../assets/images/avatar/1.jpg'),
        name: '@StreetBoy',
        title: 'Genuine Undead #3902',
        price: '3.5 ETH',
        date: 'January 29, 2025 6:0:0',
        highest: '3.55 ETH',
        showdate: false
    },
    {
        id: 2,
        mainimage: require('../../assets/images/items/2.gif'),
        image: require('../../assets/images/avatar/2.jpg'),
        name: '@CutieGirl',
        title: 'Windchime #768',
        price: '3.5 ETH',
        date: 'August 29, 2025 6:0:0',
        highest: '3.55 ETH',
        showdate: true
    },
    {
        id: 3,
        mainimage: require('../../assets/images/items/2.jpg'),
        image: require('../../assets/images/items/3.gif'),
        name: '@ButterFly',
        title: 'Probably A Label #3277',
        price: '3.5 ETH',
        date: 'January 29, 2025 6:0:0',
        highest: '3.55 ETH',
        showdate: false
    },
    {
        id: 4,
        mainimage: require('../../assets/images/items/3.jpg'),
        image: require('../../assets/images/avatar/3.jpg'),
        name: '@NorseQueen',
        title: 'Probably A Label #1711',
        price: '3.5 ETH',
        date: 'January 29, 2025 6:0:0',
        highest: '3.55 ETH',
        showdate: false
    },
    {
        id: 5,
        mainimage: require('../../assets/images/items/3.gif'),
        image: require('../../assets/images/avatar/4.jpg'),
        name: '@BigBull',
        title: 'Shibuya Scramble Punks',
        price: '3.5 ETH',
        date: 'January 29, 2025 6:0:0',
        highest: '3.55 ETH',
        showdate: false
    },
    {
        id: 6,
        mainimage: require('../../assets/images/items/4.jpg'),
        image: require('../../assets/images/avatar/5.jpg'),
        name: '@Angel',
        title: 'Probably A Label #650',
        price: '3.5 ETH',
        date: 'January 29, 2025 6:0:0',
        highest: '3.55 ETH',
        showdate: false
    },
    {
        id: 7,
        mainimage: require('../../assets/images/items/5.jpg'),
        image: require('../../assets/images/avatar/6.jpg'),
        name: '@CrazyAnyone',
        title: 'Looki#0147',
        price: '3.5 ETH',
        date: 'January 29, 2026 6:0:0',
        highest: '3.55 ETH',
        showdate: true
    },
    {
        id: 8,
        mainimage: require('../../assets/images/items/6.jpg'),
        image: require('../../assets/images/items/5.gif'),
        name: '@Princess',
        title: 'Poob #285',
        price: '3.5 ETH',
        date: 'January 29, 2025 6:0:0',
        highest: '3.55 ETH',
        showdate: false
    },
    {
        id: 9,
        mainimage: require('../../assets/images/items/8.jpg'),
        image: require('../../assets/images/avatar/7.jpg'),
        name: '@LooserBad',
        title: 'Umber Arrow',
        price: '3.5 ETH',
        date: 'January 29, 2025 6:0:0',
        highest: '3.55 ETH',
        showdate: false
    },
    {
        id: 10,
        mainimage: require('../../assets/images/items/4.gif'),
        image: require('../../assets/images/items/5.gif'),
        name: '@Princess',
        title: 'Gloam Druid',
        price: '3.5 ETH',
        date: 'January 29, 2025 6:0:0',
        highest: '3.55 ETH',
        showdate: false
    },
    {
        id: 11,
        mainimage: require('../../assets/images/items/5.gif'),
        image: require('../../assets/images/avatar/8.jpg'),
        name: '@PandaOne',
        title: 'Azuki #7421',
        price: '3.5 ETH',
        date: 'January 29, 2025 6:0:0',
        highest: '3.55 ETH',
        showdate: false
    },
    {
        id: 12,
        mainimage: require('../../assets/images/items/9.jpg'),
        image: require('../../assets/images/items/2.gif'),
        name: '@FunnyGuy',
        title: 'Wolf-Cult Vanguard',
        price: '3.5 ETH',
        date: 'January 29, 2025 6:0:0',
        highest: '3.55 ETH',
        showdate: false
    },
    {
        id: 13,
        mainimage: require('../../assets/images/blog/01.jpg'),
    },
    {
        id: 14,
        mainimage: require('../../assets/images/blog/03.jpg'),
    },
    {
        id: 15,
        mainimage: require('../../assets/images/blog/05.jpg'),
    },
    {
        id: 16,
        mainimage: require('../../assets/images/blog/07.jpg'),
    },
    {
        id: 17,
        mainimage: require('../../assets/images/blog/09.jpg'),
    },
    {
        id: 18,
        mainimage: require('../../assets/images/blog/11.jpg'),
    },
    {
        id: 19,
        mainimage: require('../../assets/images/blog/12.jpg'),
    },
    {
        id: 20,
        mainimage: require('../../assets/images/blog/14.jpg'),
    },
    {
        id: 21,
        mainimage: require('../../assets/images/blog/16.jpg'),
    },
    {
        id: 22,
        mainimage: require('../../assets/images/blog/18.jpg'),
    },
    {
        id: 23,
        mainimage: require('../../assets/images/blog/20.jpg'),
    },
    {
        id: 24,
        mainimage: require('../../assets/images/blog/22.jpg'),
    },
    {
        id: 25,
        mainimage: require('../../assets/images/blog/24.jpg'),
    },
    {
        id: 26,
        mainimage: require('../../assets/images/blog/26.jpg')
    },
    {
        id: 27,
        mainimage: require('../../assets/images/blog/02.jpg'),
    },
    {
        id: 28,
        mainimage: require('../../assets/images/blog/04.jpg'),
    },
    {
        id: 29,
        mainimage: require('../../assets/images/blog/06.jpg'),
    },
    {
        id: 30,
        mainimage: require('../../assets/images/blog/08.jpg'),
    },
    {
        id: 31,
        mainimage: require('../../assets/images/blog/10.jpg'),
    },
    {
        id: 32,
        mainimage: require('../../assets/images/blog/13.jpg'),
    },
    {
        id: 33,
        mainimage: require('../../assets/images/blog/15.jpg'),
    },
    {
        id: 34,
        mainimage: require('../../assets/images/blog/17.jpg'),
    },
    {
        id: 35,
        mainimage: require('../../assets/images/blog/19.jpg'),
    },
    {
        id: 36,
        mainimage: require('../../assets/images/blog/21.jpg'),
    },
    {
        id: 37,
        mainimage: require('../../assets/images/blog/23.jpg'),
    },
    {
        id: 38,
        mainimage: require('../../assets/images/blog/25.jpg'),
    },
    {
        id: 39,
        mainimage: require('../../assets/images/blog/01.jpg'),
    },
    {
        id: 40,
        mainimage: require('../../assets/images/blog/05.jpg')
    },
    {
        id: 41,
        mainimage: require('../../assets/images/items/1.gif'),
        type: 'Listing',
        time: '3min 50sec ago',
        title: "QUEEN'S COURT - Silver Card #72/250 was put up for sale for"
    },
])


function toggle() {
    isActive.value = !isActive.value
}

function toggle2() {
    isActive2.value = !isActive2.value
}

function toggles(Number) {
    isActiveIndex.value = Number
}


onMounted(() => {
    id.value = route.params.id
    data.value = datas.value.find((item) => item.id === parseInt(id.value))
})
</script>

<style lang="scss" scoped></style>