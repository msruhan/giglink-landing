<template>
    <div>
        <navbar />
        <!-- Start Hero -->
        <section class="relative table w-full py-32 bg-gray-50 dark:bg-slate-800">
            <div class="container">
                <div class="grid lg:grid-cols-12 grid-cols-2 pb-8 mt-10 gap-[30px] items-center">
                    <div class="lg:col-span-4">
                        <img src="../../assets/images/creator.png" alt="">
                    </div>

                    <div class="lg:col-span-8">
                        <span class="font-medium text-xl">Join with Giglink!</span>
                        <h3 class="md:text-5xl text-3xl md:leading-snug tracking-wide leading-snug font-semibold mt-2">Start Your <br> <span  class="bg-gradient-to-r from-red-600 to-violet-600 text-transparent bg-clip-text">Journey</span></h3>
                        <p class="text-slate-400 mt-4 text-lg">We are a huge marketplace dedicated to connecting great artists of all giglink with their fans and unique token collectors!</p>
                    </div>
                </div><!--end grid-->
            </div><!--end container-->

            <div class="absolute text-center z-10 bottom-5 start-0 end-0 mx-3">
                <ul class="breadcrumb tracking-[0.5px] mb-0 inline-block">
                    <li class="inline breadcrumb-item text-[15px] font-semibold duration-500 ease-in-out hover:text-violet-600">
                        <router-link to="/">Giglink</router-link>
                    </li>
                    <li class="inline breadcrumb-item text-[15px] font-semibold duration-500 ease-in-out text-violet-600"  aria-current="page">Become Creator</li>
                </ul>
            </div>
        </section><!--end section-->

        <div class="relative">
            <div
                class="shape absolute start-0 end-0 sm:-bottom-px -bottom-[2px] overflow-hidden z-1 text-white dark:text-slate-900">
                <svg class="w-full h-auto" viewBox="0 0 2880 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M0 48H1437.5H2880V0H2160C1442.5 52 720 0 720 0H0V48Z" fill="currentColor"></path>
                </svg>
            </div>
        </div>
        <!-- End Hero -->

        <section class="relative md:py-24 py-16">
            <becomecreated />
        </section>

        <switcher />

        <footers />

    </div>
</template>

<script setup>
import navbar from '@/components/navbar/navbar.vue';
import becomecreated from '@/components/become-creator.vue';
import switcher from '@/components/switcher.vue';
import footers from '@/components/footer/footer.vue';

</script>

<style lang="scss" scoped></style>