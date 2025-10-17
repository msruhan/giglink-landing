<template>
    <div>
        <div class="grid lg:grid-cols-12 md:grid-cols-2 grid-cols-1 items-center gap-[30px]">
            <div class="lg:col-span-5">
                <div class="relative">
                    <div
                        class="absolute inset-0 bg-gradient-to-r from-red-600 to-violet-600 rounded-lg -mt-[15px] -ms-[15px] h-[98%] w-[98%] -z-1">
                    </div>
                    <img src="../assets/images/about.jpg" class="rounded-lg shadow-md dark:shadow-gray-800" alt="">
                    <div class="absolute bottom-2/4 translate-y-2/4 start-0 end-0 text-center">
                        <a @click="toggle" data-type="youtube" data-id="yba7hPeTSjk" class="lightbox size-20 rounded-full shadow-lg dark:shadow-gray-800 inline-flex items-center justify-center bg-white dark:bg-slate-900 text-violet-600 cursor-pointer">
                            <i class="mdi mdi-play inline-flex items-center justify-center text-2xl"></i>
                        </a>
                    </div>
                </div>
            </div>

            <div class="lg:col-span-7">
                <div class="lg:ms-5">
                    <span class="text-violet-600 font-medium">Creative Vision & Mission</span>
                    <h3 class="mb-4 md:text-3xl text-2xl md:leading-snug leading-snug font-semibold">We develop & create <br> digital art.</h3>

                    <p class="text-slate-400 max-w-xl">We are a huge marketplace dedicated to connecting great artists ofall Giglink with their fans and unique token collectors!</p>
                    <p class="text-slate-400 max-w-xl mt-4">It seems that only fragments of the original text remain in the Lorem Ipsum texts used today. One may speculate that over the course of time certain letters were added or deleted at various positions within the text. This might also explain why one can now find slightly different versions.</p>

                    <div class="mt-6">
                        <router-link to="/contact" class="btn bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white rounded-full me-2 mt-2"><i class="uil uil-envelope"></i> Contact us</router-link>
                    </div>
                </div>
            </div>
        </div>

        <!-- iframe start  -->
        <div :class="isActive ? 'fixed' : 'hidden'" class="bg-black/[0.9] top-0 left-0 bottom-0 w-[100%] h-[100%] z-999">
            <div class="h-[100%] flex items-center justify-center">
                <iframe src="https://www.youtube.com/embed/S_CGed6E610?feature=oembed" width="700" height="500" frameborder="0"></iframe>
            </div>
            <button class="text-slate-400 absolute top-[20px] right-[20px]">
                <svg stroke="currentColor" fill="none" stroke-width="2" viewBox="0 0 24 24" stroke-linecap="round"
                    stroke-linejoin="round" class="size-5" height="1em" width="1em" xmlns="http://www.w3.org/2000/svg"
                    @click="toggle">
                    <line x1="18" y1="6" x2="6" y2="18"></line>
                    <line x1="6" y1="6" x2="18" y2="18"></line>
                </svg>
            </button>
        </div>
    <!-- iframe end  -->
</div>
</template>

<script setup>
import {ref} from 'vue';

const isActive = ref(false);

function toggle(){
    isActive.value = !isActive.value;
}
</script>

<style lang="scss" scoped></style>