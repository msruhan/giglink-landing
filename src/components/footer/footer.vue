<template>
    <!-- Start Footer -->
    <footer class="footer bg-dark-footer relative text-gray-200 dark:text-gray-200 mt-24">
        <div class="container">
            <div class="grid grid-cols-1">
                <div class="relative py-16">
                    <!-- Subscribe -->
                    <div class="relative w-full">
                        <div class="relative -top-40 bg-white dark:bg-slate-900 lg:px-8 px-6 py-10 rounded-xl shadow dark:shadow-gray-800 overflow-hidden">
                            <div class="grid md:grid-cols-2 grid-cols-1 items-center gap-[30px]">
                                <div class="md:text-start text-center z-1">
                                    <h3 class="text-[26px] font-semibold text-slate-900 dark:text-white">Subscribe to Newsletter!</h3>
                                    <p class="text-slate-400 max-w-xl mx-auto">Subscribe to get latest updates and information.</p>
                                </div>

                                <div class="subcribe-form z-1">
                                    <form class="relative max-w-lg md:ms-auto">
                                        <input type="email" id="subcribe" name="email" class="pt-4 pe-40 pb-4 ps-6 w-full h-[50px] outline-none text-slate-900 dark:text-white rounded-full bg-white dark:bg-slate-900 shadow dark:shadow-gray-800" placeholder="Enter your email :">
                                        <button type="submit" class="btn absolute top-[2px] end-[3px] h-[46px] bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white rounded-full">Subscribe</button>
                                    </form><!--end form-->
                                </div>
                            </div>

                            <div class="absolute -top-5 -start-5">
                                <div class="uil uil-envelope lg:text-[150px] text-7xl text-slate-900/5 dark:text-white/5 -rotate-45"></div>
                            </div>

                            <div class="absolute -bottom-5 -end-5">
                                <div class="uil uil-pen lg:text-[150px] text-7xl text-slate-900/5 dark:text-white/5"></div>
                            </div>
                        </div>

                        <div class="grid md:grid-cols-12 grid-cols-1 gap-[30px] -mt-24">
                            <div class="lg:col-span-4 md:col-span-12">
                                <a href="#" class="text-[22px] focus:outline-none">
                                    <img src="../../assets/images/logo-white.png" alt="">
                                </a>
                                <p class="mt-6 text-gray-300">Buy, sell and discover exclusive digital assets by the topartists of NFTs world.</p>

                            </div><!--end col-->

                            <div class="lg:col-span-2 md:col-span-4">
                                <h5 class="tracking-[1px] text-lg text-gray-100 font-semibold">Giglink</h5>
                                <ul class="list-none footer-list mt-6">
                                    <li v-for="item in giglink" :key="item" class="mt-[10px] first:mt-0"><router-link :to="item.link" class="text-[16px] text-gray-300 hover:text-gray-400 duration-500 ease-in-out"><i class="uil uil-angle-right-b me-1"></i> {{item.name}}</router-link></li>
                                </ul>
                            </div><!--end col-->

                            <div class="lg:col-span-3 md:col-span-4">
                                <h5 class="tracking-[1px] text-lg text-gray-100 font-semibold">Usefull Links</h5>
                                <ul class="list-none footer-list mt-6">
                                    <li class="mt-[10px] first:mt-0" v-for="item in usefull" :key="item"><router-link :to="item.link" class="text-[16px] text-gray-300 hover:text-gray-400 duration-500 ease-in-out"><i class="uil uil-angle-right-b me-1"></i> {{item.name}}</router-link></li>
                                </ul>
                            </div><!--end col-->

                            <div class="lg:col-span-3 md:col-span-4">
                                <h5 class="tracking-[1px] text-lg text-gray-100 font-semibold">Download the Giglink app</h5>

                                <ul class="list-none mt-6">
                                    <li class="inline me-1"><img src="../../assets/images/app.png" class="h-9 inline-block" alt=""></li>
                                    <li class="inline"><img src="../../assets/images/playstore.png" class="h-9 inline-block" alt=""></li>
                                </ul>

                                <div class="mt-6">
                                    <h5 class="tracking-[1px] text-lg text-gray-100 font-semibold">Contact Details</h5>

                                    <div class="flex mt-6">
                                        <i data-feather="mail" class="size-5 text-violet-600 me-3 mt-1"></i>
                                        <div class="">
                                            <a href="mailto:contact@example.com" class="text-[16px] text-gray-300 hover:text-gray-400 duration-500 ease-in-out">contact@example.com</a>
                                        </div>
                                    </div>

                                    <div class="flex mt-6">
                                        <i data-feather="phone" class="size-5 text-violet-600 me-3 mt-1"></i>
                                        <div class="">
                                            <a href="tel:+152534-468-854" class="text-[16px] text-gray-300 hover:text-gray-400 duration-500 ease-in-out">+152 534-468-854</a>
                                        </div>
                                    </div>
                                </div>
                            </div><!--end col-->
                        </div><!--end grid-->
                    </div>
                    <!-- Subscribe -->
                </div>
            </div>
        </div><!--end container-->

        <div class="py-[30px] px-0 border-t border-gray-800 dark:border-gray-700">
            <div class="container text-center">
                <div class="grid md:grid-cols-2 items-center gap-6">
                    <div class="md:text-start text-center">
                        <p class="mb-0 text-gray-300">© {{date}} Giglink. Design & Develop with <i class="mdi mdi-heart text-red-600"></i> by <a href="https://shreethemes.in/" target="_blank" class="text-reset">Shreethemes</a>.
                        </p>
                    </div>

                    <ul class="list-none md:text-end text-center">
                        <li v-for="item in social" :key="item" class="inline me-1"><a :href="item.link" target="_blank" class="btn btn-icon btn-sm border border-gray-800 rounded-md hover:border-violet-600 dark:hover:border-violet-600 hover:bg-violet-600 dark:hover:bg-violet-600"><i :class="item.icon" title="Buy Now"></i></a></li>
                    </ul><!--end icon-->
                </div><!--end grid-->
            </div><!--end container-->
        </div>
    </footer><!--end footer-->
    <!-- End Footer -->
</template>

<script setup>

const date = new Date().getFullYear()

const giglink = [
    {
        link: '/explore-one',
        name: 'Explore Item'
    },
    {
        link: '/auction',
        name: 'Live Auction'
    },
    {
        link: '/activity',
        name: 'Activities'
    },
    {
        link: '/wallet',
        name: 'Wallets'
    },
    {
        link: '/creators',
        name: 'Creators'
    },
]

const usefull = [
    {
        link: '/aboutus',
        name: 'About Us'
    },
    {
        link: '/blogs',
        name: 'Blog & News'
    },
    {
        link: '/terms',
        name: 'Terms & Condition'
    },
    {
        link: '/privacy',
        name: 'Privacy policy'
    },
    {
        link: '/login',
        name: 'Login'
    },
    {
        link: '/contact',
        name: 'Contact Us'
    },
]

const social = [
    {
        link: 'https://1.envato.market/giglink-vue',
        icon: 'uil uil-shopping-cart align-middle'
    },
    {
        link: 'https://dribbble.com/shreethemes',
        icon: 'uil uil-dribbble align-middle'
    },
    {
        link: 'https://www.behance.net/shreethemes',
        icon: 'uil uil-behance'
    },
    {
        link: 'http://linkedin.com/company/shreethemes',
        icon: 'uil uil-linkedin'
    },
    {
        link: 'https://www.facebook.com/shreethemes',
        icon: 'uil uil-facebook-f align-middle'
    },
    {
        link: 'https://www.instagram.com/shreethemes/',
        icon: 'uil uil-instagram align-middle'
    },
    {
        link: 'https://twitter.com/shreethemes',
        icon: 'uil uil-twitter align-middle'
    },
    {
        link: 'mailto:support@shreethemes.in',
        icon: 'uil uil-envelope align-middle'
    },
]

</script>

<style lang="scss" scoped></style>