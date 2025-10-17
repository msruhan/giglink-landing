<template>
    <div>
        <navbar />
        <!-- Start -->
        <section class="relative lg:pt-24 pt-[74px] overflow-hidden">
            <div class="container-fluid lg:px-10 md:px-3 relative overflow-hidden">
                <span class="absolute blur-[200px] w-[600px] h-[600px] rounded-full top-1/2 start-1/2 ltr:-translate-x-1/2 rtl:translate-x-1/2 -translate-y-1/2 bg-gradient-to-tl from-red-600/40 to-violet-600/40 dark:from-red-600/60 dark:to-violet-600/60"></span>
                <div class="lg:py-24 py-[74px] md:rounded-lg shadow dark:shadow-gray-800 bg-violet-700/10 dark:bg-violet-600/20">
                    <div class="container">
                        <div class="grid md:grid-cols-12 grid-cols-1 items-center gap-[30px]">
                            <div class="md:col-span-7">
                                <div class="md:me-6">
                                    <h4 class="font-bold lg:leading-snug leading-snug text-4xl lg:text-6xl mb-4"><span class="bg-gradient-to-l from-red-600 to-violet-600 text-transparent bg-clip-text">The Place Where Technicians</span> Connect, <br>Trade & Grow</h4>
                                    <p class="text-lg max-w-xl">Marketplace dan Komunitas Teknisi Smartphone Indonesia — Jual alat servis, cari jasa, ikuti workshop, dan diskusi bareng ribuan teknisi aktif!</p>

                                    <div class="mt-6">
                                        <router-link to="/explore-two" class="btn bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white rounded-full me-2 mt-2">Explore Marketplace</router-link>
                                        <router-link to="/upload-work" class="btn bg-transparent hover:bg-violet-600 border-violet-600 text-violet-600 hover:text-white rounded-full mt-2">Join Community</router-link>
                                    </div>
                                </div>
                                <div
                                    class="overflow-hidden after:content-[''] after:absolute after:h-10 after:w-10 after:bg-violet-600/10 dark:after:bg-violet-600/30 after:-bottom-[50px] after:start-[30%] after:-z-1 after:rounded-full after:animate-ping">
                                </div>
                            </div><!--end col-->

                            <nftslider />
                        </div><!--end grid-->
                    </div><!--end container-->
                </div><!--end -->
            </div><!--end container fluid-->
        </section><!--end section-->
        <!-- Statistik -->
        <!-- Searchbar di tengah antar section -->
        <div class="flex justify-center -mt-10">
            <searchbar />
        </div>

          <div class="container mt-10">
            <div class="grid grid-cols-2 md:grid-cols-4 gap-6 text-center">
                <div class="bg-white dark:bg-slate-900 rounded-lg shadow p-6 flex flex-col items-center">
                    <span class="mdi mdi-account-group text-4xl text-violet-600 mb-2"></span>
                    <div class="text-3xl font-bold text-violet-600 mb-2">4000+</div>
                    <div class="text-slate-600 dark:text-slate-200">Anggota</div>
                </div>
                <div class="bg-white dark:bg-slate-900 rounded-lg shadow p-6 flex flex-col items-center">
                    <span class="mdi mdi-school text-4xl text-violet-600 mb-2"></span>
                    <div class="text-3xl font-bold text-violet-600 mb-2">100+</div>
                    <div class="text-slate-600 dark:text-slate-200">Workshop</div>
                </div>
                <div class="bg-white dark:bg-slate-900 rounded-lg shadow p-6 flex flex-col items-center">
                    <span class="mdi mdi-cart text-4xl text-violet-600 mb-2"></span>
                    <div class="text-3xl font-bold text-violet-600 mb-2">100+</div>
                    <div class="text-slate-600 dark:text-slate-200">Produk Terjual</div>
                </div>
                <div class="bg-white dark:bg-slate-900 rounded-lg shadow p-6 flex flex-col items-center">
                    <span class="mdi mdi-shield-check text-4xl text-violet-600 mb-2"></span>
                    <div class="text-3xl font-bold text-violet-600 mb-2">100+</div>
                    <div class="text-slate-600 dark:text-slate-200">Transaksi Rekber</div>
                </div>
            </div>
        </div>
        <!-- End -->
        <section class="relative md:py-24 py-16">
            <div class="container">
                <div class="md:flex justify-between items-center">
                    <div class="md:w-10/12 md:text-start text-center">
                        <h3 class="md:text-[30px] text-[26px] font-semibold">Best Technicians
                            <select
                                class="form-select z-2 text-violet-600 focus-visible:outline-none bg-transparent border-0 focus:ring-transparent"
                                aria-label="Default select example">
                                <option class="text-lg font-medium">Week</option>
                                <option class="text-lg font-medium">Month</option>
                                <option class="text-lg font-medium">Year</option>
                            </select>
                        </h3>
                        <p class="text-slate-400">Best sellers of the week's</p>
                    </div>
                    <div class="md:w-2/12 text-end md:block hidden">
                        <router-link to="/explore-teknisi" class="btn btn-link text-[16px] font-medium hover:text-violet-600 after:bg-violet-600 duration-500 ease-in-out">Semua Teknisi <i class="uil uil-arrow-right"></i></router-link>
                    </div>
                </div><!--end grid-->

                <creators />

            </div>

            <div class="container mt-16">
                <div class="md:flex justify-between items-center">
                    <div class="md:w-10/12 md:text-start text-center">
                        <h3 class="md:text-[30px] text-[26px] font-semibold">Best Workshops
                            <select
                                class="form-select z-2 text-violet-600 focus-visible:outline-none bg-transparent border-0 focus:ring-transparent"
                                aria-label="Default select example">
                                <option class="text-lg font-medium">Week</option>
                                <option class="text-lg font-medium">Month</option>
                                <option class="text-lg font-medium">Year</option>
                            </select>
                        </h3>
                        <p class="text-slate-400">Best Workshop of the week's</p>
                    </div>
                    <div class="md:w-2/12 text-end md:block hidden">
                        <router-link to="/explore-workshop" class="btn btn-link text-[16px] font-medium hover:text-violet-600 after:bg-violet-600 duration-500 ease-in-out">Semua Workshop <i class="uil uil-arrow-right"></i></router-link>
                    </div>
                </div>

                <best-workshop-slider />

            </div>
            

            <div class="container md:mt-24 mt-16">
                <destination />
            </div>

           

            <discover :discover=true :moreitem=true />

            <blog />

            <testimoni />

            <getintouch />

            

        </section>
        

        <switcher />
        
        <footers />
    </div>
</template>

<script setup>
import navbar from '@/components/navbar/navbar.vue';
import nftslider from '@/components/nft-slider.vue'
import switcher from '@/components/switcher.vue';
import testimoni from '@/components/testimoni.vue';
import searchbar from '@/components/nft-searchbar.vue';
import creators from '@/components/best-creators.vue';
import destination from '@/components/giglink-destination.vue';
import discover from '@/components/discover-lisensi.vue';
import blog from '@/components/blog/latest-blog.vue';
import getintouch from '@/components/get-in-touch.vue';
import footers from '@/components/footer/footer.vue'
import bestWorkshopSlider from '@/components/best-workshop-slider.vue';

</script>
