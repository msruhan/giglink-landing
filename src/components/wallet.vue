<template>
    <div>
        <div class="grid xl:grid-cols-4 lg:grid-cols-3 md:grid-cols-2 grid-cols-1 gap-[30px]">
            <div v-for="item in datas" :key="item" class="group relative rounded-xl bg-white dark:bg-slate-900 shadow dark:shadow-gray-800 p-6 text-center mt-10 hover:shadow-md dark:hover:shadow-gray-800 transition-all duration-500">
                <div class="relative -mt-16">
                    <img :src="item.image" class="bg-white dark:bg-slate-900 size-20 rounded-full shadow-md dark:shadow-gray-800 mx-auto p-3" alt="">
                
                    <h5 class="text-lg font-semibold mt-5">{{item.name}}</h5>

                    <p class="text-slate-400 mt-3">{{item.title}} <a @click="toggle" href="javascript:void(0)" data-modal-toggle="loginform" class="btn btn-link text-violet-600 hover:text-violet-600 after:bg-violet-600 duration-500 ease-in-out">here <i class="uil uil-arrow-right"></i></a></p>
                </div>
            </div><!--end content-->
        </div><!--end grid-->


            <!-- Start Modal -->
        <div :class="isActive ? 'fixed' : 'hidden'" id="loginform" tabindex="-1" class="z-50 flex justify-center items-center overflow-hidden inset-0 m-auto">
            <div class="relative w-full h-auto max-w-md p-4">
                <div class="relative bg-white dark:bg-slate-900 rounded-lg shadow dark:shadow-gray-800">
                    <div class="flex justify-between items-center px-6 py-4 border-b border-gray-100 dark:border-gray-700">
                        <h5 class="text-xl font-semibold">Login</h5>
                        <button type="button" class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm p-1.5 ms-auto inline-flex items-center dark:hover:bg-gray-800 dark:hover:text-white" data-modal-toggle="loginform">
                            <svg @click="toggle" class="size-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>  
                        </button>
                    </div>
                    <div class="p-6">
                        <form class="text-start">
                            <div class="grid grid-cols-1">
                                <div class="mb-4">
                                    <label class="font-semibold" for="LoginEmail">Email Address:</label>
                                    <input id="LoginEmail" type="email" class="form-input w-full text-[15px] py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-violet-600 dark:border-gray-800 dark:focus:border-violet-600 focus:ring-0 mt-3" placeholder="name@example.com">
                                </div>

                                <div class="mb-4">
                                    <label class="font-semibold" for="LoginPassword">Password:</label>
                                    <input id="LoginPassword" type="password" class="form-input w-full text-[15px] py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-violet-600 dark:border-gray-800 dark:focus:border-violet-600 focus:ring-0 mt-3" placeholder="Password:">
                                </div>

                                <div class="flex justify-between mb-4">
                                    <div class="inline-flex items-center mb-0">
                                        <input class="form-checkbox rounded border-gray-200 dark:border-gray-800 text-violet-600 focus:border-violet-600/30 focus:ring focus:ring-offset-0 focus:ring-violet-600/20 focus:ring-opacity-50 me-2" type="checkbox" value="" id="RememberMe">
                                        <label class="form-checkbox-label text-slate-400" for="RememberMe">Remember me</label>
                                    </div>
                                    <p class="text-slate-400 mb-0"><router-link to="/reset-password" class="text-slate-400">Forgot password ?</router-link></p>
                                </div>

                                <div class="mb-4">
                                    <input type="submit" class="btn bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white rounded-full w-full" value="Login / Sign in">
                                </div>

                                <div class="text-center">
                                    <span class="text-slate-400 me-2">Don't have an account ?</span> <router-link to="/signup" class="text-black dark:text-white font-bold">Sign Up</router-link>
                                </div>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
        <!-- End Modal -->
    </div>
</template>

<script setup>
import {ref} from 'vue'

const isActive = ref(false)

const datas = ref([
    {
        image: require('../assets/images/wallet/metamask.png'),
        name: 'MetaMask',
        title: 'Learn about how to get the wallet and much more clicking'
    },
    {
        image: require('../assets/images/wallet/alpha.png'),
        name: 'Alpha',
        title: 'Learn about how to get the wallet and much more clicking'
    },
    {
        image: require('../assets/images/wallet/binance.png'),
        name: 'Binance',
        title: 'Learn about how to get the wallet and much more clicking'
    },
    {
        image: require('../assets/images/wallet/bitski.png'),
        name: 'Bitski',
        title: 'Learn about how to get the wallet and much more clicking'
    },
    {
        image: require('../assets/images/wallet/coinbase.png'),
        name: 'Coinbase',
        title: 'Learn about how to get the wallet and much more clicking'
    },
    {
        image: require('../assets/images/wallet/enjin.png'),
        name: 'Enjin',
        title: 'Learn about how to get the wallet and much more clicking'
    },
    {
        image: require('../assets/images/wallet/formatic.png'),
        name: 'Formatic',
        title: 'Learn about how to get the wallet and much more clicking'
    },
    {
        image: require('../assets/images/wallet/pionex.png'),
        name: 'Pionex',
        title: 'Learn about how to get the wallet and much more clicking'
    },
    {
        image: require('../assets/images/wallet/torus.png'),
        name: 'Torus',
        title: 'Learn about how to get the wallet and much more clicking'
    },
    {
        image: require('../assets/images/wallet/trustwallet.png'),
        name: 'Trustwallet',
        title: 'Learn about how to get the wallet and much more clicking'
    },
    {
        image: require('../assets/images/wallet/wallet-connect.png'),
        name: 'Wallet Connect',
        title: 'Learn about how to get the wallet and much more clicking'
    },
])

function toggle(){
    isActive.value = !isActive.value
}

</script>

<style lang="scss" scoped>

</style>