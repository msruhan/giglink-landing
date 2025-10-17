<template>
    <div>
        <div class="container">
            <div class="grid grid-cols-1 lg:grid-cols-3 md:grid-cols-2 gap-[30px]">
                <div v-for="item in datas" :key="item" class="text-center px-6 mt-6">
                    <div class="size-20 bg-violet-600/5 text-violet-600 rounded-full text-3xl flex align-middle justify-center items-center shadow-sm dark:shadow-gray-800 mx-auto">
                        <i :class="item.icon"></i>
                    </div>

                    <div class="content mt-7">
                        <h5 class="title text-xl font-semibold">{{ item.name }}</h5>
                        <p class="text-slate-400 mt-3">{{ item.title }}</p>

                        <div class="mt-5">
                            <a :href="item.link" class="btn btn-link text-violet-600 hover:text-violet-600 after:bg-violet-600 duration-500 ease-in-out">{{item.name2 }}</a>
                        </div>
                    </div>
                </div>

                <div class="text-center px-6 mt-6">
                    <div class="size-20 bg-violet-600/5 text-violet-600 rounded-full text-3xl flex align-middle justify-center items-center shadow-sm dark:shadow-gray-800 mx-auto">
                        <i class="uil uil-map-marker"></i>
                    </div>

                    <div class="content mt-7">
                        <h5 class="title text-xl font-semibold">Location</h5>
                        <p class="text-slate-400 mt-3">C/54 Northwest Freeway, Suite 558, <br> Houston, USA 485</p>

                        <div class="mt-5">
                            <a @click="toggle" data-type="iframe" class="video-play-icon read-more lightbox btn btn-link text-violet-600 hover:text-violet-600 after:bg-violet-600 duration-500 ease-in-out cursor-pointer">View on Google map</a>
                        </div>
                    </div>
                </div>
            </div><!--end grid-->
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

        <div class="container md:mt-24 mt-16">
            <div class="grid md:grid-cols-12 grid-cols-1 items-center gap-[30px]">
                <div class="lg:col-span-7 md:col-span-6 order-1 md:order-2">
                    <img src="../assets/images/contact.svg" alt="">
                </div>

                <div class="lg:col-span-5 md:col-span-6 mt-8 md:mt-0 order-2 md:order-1">
                    <div class="lg:me-5">
                        <div class="bg-white dark:bg-slate-900 rounded-md shadow dark:shadow-gray-800 p-6">
                            <h3 class="mb-6 text-2xl leading-snug font-medium">Get in touch !</h3>

                            <form>
                                <div class="grid lg:grid-cols-12 lg:gap-6">
                                    <div class="lg:col-span-6 mb-5">
                                        <div class="text-start">
                                            <label for="name" class="font-semibold">Your Name:</label>
                                            <input name="name" id="name" type="text" class="form-input w-full text-[15px] py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-violet-600 dark:border-gray-800 dark:focus:border-violet-600 focus:ring-0 mt-2" placeholder="Name :">
                                        </div>
                                    </div>

                                    <div class="lg:col-span-6 mb-5">
                                        <div class="text-start">
                                            <label for="email" class="font-semibold">Your Email:</label>
                                            <input name="email" id="email" type="email" class="form-input w-full text-[15px] py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-violet-600 dark:border-gray-800 dark:focus:border-violet-600 focus:ring-0 mt-2" placeholder="Email :">
                                        </div>
                                    </div>
                                </div>

                                <div class="grid grid-cols-1">
                                    <div class="mb-5">
                                        <div class="text-start">
                                            <label for="subject" class="font-semibold">Your Question:</label>
                                            <input name="subject" id="subject" class="form-input w-full text-[15px] py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-violet-600 dark:border-gray-800 dark:focus:border-violet-600 focus:ring-0 mt-2" placeholder="Subject :">
                                        </div>
                                    </div>

                                    <div class="mb-5">
                                        <div class="text-start">
                                            <label for="comments" class="font-semibold">Your Comment:</label>
                                            <textarea name="comments" id="comments" class="form-input w-full text-[15px] py-2 px-3 h-28 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-2xl outline-none border border-gray-200 focus:border-violet-600 dark:border-gray-800 dark:focus:border-violet-600 focus:ring-0 mt-2"
                                                placeholder="Message :"></textarea>
                                        </div>
                                    </div>
                                </div>
                                <button type="submit" id="submit" name="send" class="btn bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white rounded-full justify-center flex items-center">Send Message</button>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </div><!--end container-->

        <div class="container-fluid relative">
            <div class="grid grid-cols-1">
                <div class="w-full leading-[0] border-0">
                    <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d39206.002432144705!2d-95.4973981212445!3d29.709510002925988!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x8640c16de81f3ca5%3A0xf43e0b60ae539ac9!2sGerald+D.+Hines+Waterwall+Park!5e0!3m2!1sen!2sin!4v1566305861440!5m2!1sen!2sin" style="border:0" class="w-full h-[500px]" allowfullscreen></iframe>
                </div>
            </div><!--end grid-->
        </div><!--end container-->
    </div>
</template>

<script setup>
import { ref } from 'vue'

const isActive = ref(false)

const datas = ref([
    {
        icon: 'uil uil-phone',
        name: 'Phone',
        title: 'The phrasal sequence of the is now so that many campaign and benefit',
        name2: '+152 534-468-854',
        link: 'tel:+152534-468-854'
    },
    {
        icon: 'uil uil-envelope',
        name: 'Email',
        title: 'The phrasal sequence of the is now so that many campaign and benefit',
        name2: 'contact@example.com',
        link: 'mailto:contact@example.com'
    },
])

function toggle() {
    isActive.value = !isActive.value

}

</script>

<style lang="scss" scoped></style>