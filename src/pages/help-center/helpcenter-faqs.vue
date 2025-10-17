<template>
    <div>
        <navbar :navLight="'nav-light'" :logoLight=true />
        <!-- Start Hero -->
        <section class="relative table w-full py-36 bg-[url('../../assets/images/bg/bg1.jpg')] bg-bottom bg-no-repeat">
            <div class="absolute inset-0 bg-gradient-to-b from-transparent to-slate-900"></div>
            <div class="container">
                <div class="grid grid-cols-1 pb-8 text-center mt-10">
                    <h3 class="md:text-3xl text-2xl md:leading-snug tracking-wide leading-snug font-medium text-white">
                        Frequently Asked Questions</h3>

                </div><!--end grid-->
            </div><!--end container-->

            <div class="absolute text-center z-10 bottom-5 start-0 end-0 mx-3">
                <ul class="breadcrumb tracking-[0.5px] breadcrumb-light mb-0 inline-block">
                    <li class="inline breadcrumb-item text-[15px] font-semibold duration-500 ease-in-out text-white/50 hover:text-white">
                        <router-link to="/">Giglink</router-link>
                    </li>
                    <li class="inline breadcrumb-item text-[15px] font-semibold duration-500 ease-in-out text-white/50 hover:text-white">
                        <router-link to="/helpcenter-overview">Helpcenter</router-link>
                    </li>
                    <li class="inline breadcrumb-item text-[15px] font-semibold duration-500 ease-in-out text-white" aria-current="page">FAQs</li>
                </ul>
            </div>
        </section><!--end section-->
        <div class="relative">
            <div class="shape absolute start-0 end-0 sm:-bottom-px -bottom-[2px] overflow-hidden z-1 text-white dark:text-slate-900">
                <svg class="w-full h-auto" viewBox="0 0 2880 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M0 48H1437.5H2880V0H2160C1442.5 52 720 0 720 0H0V48Z" fill="currentColor"></path>
                </svg>
            </div>
        </div>
        <!-- End Hero -->

        <!-- Start Section-->
        <section class="relative md:py-24 py-16">
            <div class="container">
                <div class="grid md:grid-cols-12 grid-cols-1 gap-[30px]">
                    <div class="lg:col-span-4 md:col-span-5">
                        <div class="rounded-md shadow dark:shadow-gray-800 p-6 sticky top-20">
                            <ul class="list-none sidebar-nav mb-0 py-0" id="navmenu-nav">
                                <li class="navbar-item p-0" :class="activeId === 'tech' ? 'active' : ''"><a href="#tech" class="text-base font-medium navbar-link">Buying Questions</a></li>
                                <li class="navbar-item mt-3 p-0" :class="activeId === 'general' ? 'active' : ''"><a href="#general" class="text-base font-medium navbar-link">General Questions</a></li>
                                <li class="navbar-item mt-3 p-0" :class="activeId === 'payment' ? 'active' : ''"><a href="#payment" class="text-base font-medium navbar-link">Payments Questions</a></li>
                                <li class="navbar-item mt-3 p-0" :class="activeId === 'support' ? 'active' : ''"><a href="#support" class="text-base font-medium navbar-link">Support Questions</a></li>
                            </ul>
                        </div>
                    </div>

                    <div class="lg:col-span-8 md:col-span-7">
                        <div id="tech" class="scroll-div">
                            <h5 class="text-2xl font-semibold">Buying Product</h5>

                            <div id="accordion-collapseone" data-accordion="collapse" class="mt-6">
                                <questions />
                            </div>
                        </div>

                        <div id="general" class="mt-8 scroll-div">
                            <h5 class="text-2xl font-semibold">General Questions</h5>

                            <div id="accordion-collapsetwo" data-accordion="collapse" class="mt-6">
                                <questions />
                            </div>
                        </div>

                        <div id="payment" class="mt-8 scroll-div">
                            <h5 class="text-2xl font-semibold">Payments Questions</h5>

                            <div id="accordion-collapsethree" data-accordion="collapse" class="mt-6">
                                <questions />
                            </div>
                        </div>

                        <div id="support" class="mt-8 scroll-div">
                            <h5 class="text-2xl font-semibold">Support Questions</h5>

                            <div id="accordion-collapsefour" data-accordion="collapse" class="mt-6">
                                <questions />
                            </div>
                        </div>
                    </div>
                </div><!--end grid-->
            </div><!--end container-->

            <getintouch />
            
        </section><!--end section-->
        <!-- End Section-->

        <switcher />
        <footers />
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import navbar from '@/components/navbar/navbar.vue';
import switcher from '@/components/switcher.vue';
import footers from '@/components/footer/footer.vue';
import questions from '@/components/questions.vue';
import getintouch from '@/components/get-in-touch.vue'

const activeId = ref('');

onMounted(() => {
    window.addEventListener('scroll', checkVisibleDiv);
})

function checkVisibleDiv() {
    const windowHeight = window.innerHeight;
    const divElements = document.querySelectorAll('.scroll-div');
    divElements.forEach(div => {
        const rect = div.getBoundingClientRect();
        const isVisible = (rect.top >= 0 && rect.bottom <= windowHeight);
        if (isVisible) {
            activeId.value = div.id;
        }
    });
}

</script>

<style lang="scss" scoped></style>