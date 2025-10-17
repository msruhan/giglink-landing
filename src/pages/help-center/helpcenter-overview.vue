<template>
    <div>
        <navbar :navLight="'nav-light'" :logoLight=true />
        <!-- Start Hero -->
        <section class="relative table w-full py-36 bg-[url('../../assets/images/bg/bg1.jpg')] bg-bottom bg-no-repeat">
            <div class="absolute inset-0 bg-gradient-to-b from-transparent to-slate-900"></div>
            <div class="container">
                <div class="grid grid-cols-1 pb-8 text-center mt-10">
                    <h3 class="mb-6 md:text-4xl text-3xl md:leading-snug leading-snug font-semibold text-white">Hello ! <br>
                        How can we help you?</h3>

                    <div class="text-center subcribe-form mt-4 pt-2">
                        <form class="relative mx-auto max-w-xl">
                            <input type="text" id="help" name="name"
                                class="pt-4 pe-40 pb-4 ps-6 w-full h-[50px] outline-none text-slate-900 dark:text-white rounded-full bg-white/70 dark:bg-slate-900/70 shadow dark:shadow-gray-800"
                                placeholder="Search your questions or topic...">
                            <button type="submit"
                                class="btn absolute top-[2px] end-[3px] h-[46px] bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white rounded-full">Search</button>
                        </form><!--end form-->
                    </div>
                </div><!--end grid-->
            </div><!--end container-->

            <div class="absolute text-center z-10 bottom-5 start-0 end-0 mx-3">
                <ul class="breadcrumb tracking-[0.5px] breadcrumb-light mb-0 inline-block">
                    <li
                        class="inline breadcrumb-item text-[15px] font-semibold duration-500 ease-in-out text-white/50 hover:text-white">
                        <router-link to="/">Giglink</router-link>
                    </li>
                    <li class="inline breadcrumb-item text-[15px] font-semibold duration-500 ease-in-out text-white"
                        aria-current="page">Helpcenter</li>
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
        <!-- Start -->
        <section class="relative md:py-24 py-16">
            <helpneed />
            <div class="container md:mt-24 mt-16">
                <div class="grid grid-cols-1 pb-8 text-center">
                    <h3 class="mb-4 md:text-3xl text-2xl md:leading-snug leading-snug font-semibold">Get Started</h3>
                    <p class="text-slate-400 max-w-xl mx-auto">We are a huge marketplace dedicated to connecting great artists of all Giglink with their fans and unique token collectors!</p>
                </div><!--end grid-->

                <div class="flex justify-center mt-8">
                    <div class="lg:w-2/3">
                        <div id="accordion-collapseone" data-accordion="collapse" class="mt-6">
                            <questions />
                        </div>
                    </div>
                </div>
            </div>
            <getintouch />
        </section>
        <switcher />
        <footers />
    </div>
</template>

<script setup>
import navbar from '@/components/navbar/navbar.vue';
import helpneed from '@/components/help-need.vue';
import questions from '@/components/questions.vue';
import getintouch from '@/components/get-in-touch.vue';
import switcher from '@/components/switcher.vue';
import footers from '@/components/footer/footer.vue'

</script>

<style lang="scss" scoped></style>