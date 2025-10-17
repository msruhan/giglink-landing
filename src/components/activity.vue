<template>
    <div class="md:flex">
        <div class="lg:w-3/5 md:w-1/2 md:pe-4">
            <div v-for="item in datas" :key="item" class="group rounded-xl bg-white dark:bg-slate-900 shadow hover:shadow-md dark:shadow-gray-800 dark:hover:shadow-gray-800 overflow-hidden ease-in-out duration-500 w-full mx-auto lg:max-w-2xl mt-[30px] first:mt-0">
                <div class="lg:flex">
                    <div class="relative md:shrink-0">
                        <img class="h-full w-full object-cover lg:w-48" :src="item.mainimage" alt="">
                    </div>
                    <div class="p-6 w-full">
                        <ul class="flex justify-between items-center list-none pb-6">
                            <li class="block items-center">
                                <span class="bg-slate-900 text-white dark:bg-slate-800 text-[12px] px-2.5 py-1 font-semibold rounded-full h-5">{{item.type}}</span>
                                <span class="text-slate-400 text-sm ms-2">{{item.time}}</span>
                            </li>
                            <li>
                                <a href="javascript:void(0)" class="text-lg rounded-full text-gray-300 dark:text-gray-800 hover:text-red-600 focus:text-red-600 dark:hover:text-red-600 dark:focus:text-red-600"><i class="mdi mdi-heart"></i></a>
                            </li>
                        </ul>

                        <router-link :to="{name: 'item-detail', params: {id: item.id}}" class="font-semibold">{{item.title}} </router-link>

                        <div class="pt-6">
                            <router-link :to="{name: 'item-detail', params: {id: item.id}}" class="btn btn-sm rounded-full bg-violet-600/5 hover:bg-violet-600 border-violet-600/10 hover:border-violet-600 text-violet-600 hover:text-white">Buy now for $15</router-link>
                        </div>
                    </div>
                </div>
            </div>
            <!-- End Content -->
            <div class="mt-[30px] text-center">
                <a href="" class="text-violet-600"><i class="mdi mdi-loading mdi-spin"></i> More Items</a>
            </div>
        </div>

        <div class="lg:w-2/5 md:w-1/2 md:ps-4">
            <div class="sticky top-20">
                <h5 class="text-lg font-semibold">Filter by</h5>

                <div class="form-icon relative mt-4">
                    <i class="uil uil-search text-lg absolute top-1/2 -translate-y-1/2 start-3"></i>
                    <input type="text" class="form-input w-full text-[15px] ps-10 py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-violet-600 dark:border-gray-800 dark:focus:border-violet-600 focus:ring-0" name="s" id="searchItem2" placeholder="Search...">
                </div>

                <h5 class="text-lg font-semibold mt-6">Collection Type</h5>

                <ul class="list-none mt-4">
                    <li v-for="item in types" :key="item" class="inline-block m-2"><a href="" class="px-3 py-1.5 text-slate-400 hover:text-white dark:hover:text-white bg-gray-50 dark:bg-slate-800 text-sm hover:bg-violet-600 dark:hover:bg-violet-600 font-semibold rounded-lg shadow dark:shadow-gray-800 transition-all duration-500 ease-in-out"><i :class="item.icon"></i> {{item.name}}</a></li>
                    
                </ul>
            </div>
        </div>
    </div>
</template>

<script setup>

const datas = [
    {
        id: 41,
        mainimage: require('../assets/images/items/1.gif'),
        type: 'Listing',
        time: '3min 50sec ago',
        title: "QUEEN'S COURT - Silver Card #72/250 was put up for sale for"
    },
    {
        id: 1,
        mainimage: require('../assets/images/items/1.jpg'),
        type: 'Sale',
        time: '3min 50sec ago',
        title: 'ethkun #5001 was sold for $9.27.'
    },
    {
        id: 3,
        mainimage: require('../assets/images/items/2.jpg'),
        type: 'Offer',
        time: '3min 50sec ago',
        title: 'A global offer of $100.00 was placed for FACES'
    },
    {
        id: 4,
        mainimage: require('../assets/images/items/3.jpg'),
        type: 'Deposit',
        time: '3min 50sec ago',
        title: 'Anatomy Science Ape Club #1113 was sold for $32.87.'
    },
    {
        id: 2,
        mainimage: require('../assets/images/items/2.gif'),
        type: 'Listing',
        time: '3min 50sec ago',
        title: 'Swiss Army Man #16/30 was sold for $600.00.'
    },
    {
        id: 6,
        mainimage: require('../assets/images/items/4.jpg'),
        type: 'Sale',
        time: '3min 50sec ago',
        title: 'Unsupervised — Machine Hallucinations — MoMA Dreams — I by Refik Anadol #84/100, 1 AP was sold for $1,210.16.'
    },
    {
        id: 5,
        mainimage: require('../assets/images/items/3.gif'),
        type: 'Listing',
        time: '3min 50sec ago',
        title: '3D Bear #7333 was put up for sale for $8.00.'
    },
]

const types = [
    {
        icon: 'uil uil-wallet me-1',
        name: 'Purchased'
    },
    {
        icon: 'uil uil-tag-alt me-1',
        name: 'Sales'
    },
    {
        icon: 'uil uil-fire me-1',
        name: 'Burns'
    },
    {
        icon: 'uil uil-heart me-1',
        name: 'Likes'
    },
    {
        icon: 'uil uil-browser me-1',
        name: 'Bids'
    },
    {
        icon: 'uil uil-users-alt me-1',
        name: 'Following'
    },
    {
        icon: 'uil uil-list-ui-alt me-1',
        name: 'Listing'
    },
    {
        icon: 'uil uil-music me-1',
        name: 'Music'
    },
    {
        icon: 'uil uil-camera me-1',
        name: 'Video'
    },
    {
        icon: 'uil uil-illustration me-1',
        name: 'Illustration'
    },
]
</script>

<style lang="scss" scoped>

</style>