<template>
    <div>
        <navbar :navLight="'nav-light'" :logoLight=true />

        <!-- Start Hero -->
        <section class="relative table w-full py-36 bg-[url('../../assets/images/bg/bg1.jpg')] bg-bottom bg-no-repeat">
            <div class="absolute inset-0 bg-gradient-to-b from-transparent to-slate-900"></div>
            <div class="container">
                <div class="grid grid-cols-1 pb-8 text-center mt-10">
                    <h3 class="md:text-3xl text-2xl md:leading-snug tracking-wide leading-snug font-medium text-white">Blog & News</h3>
                </div><!--end grid-->
            </div><!--end container-->

            <div class="absolute text-center z-10 bottom-5 start-0 end-0 mx-3">
                <ul class="breadcrumb tracking-[0.5px] breadcrumb-light mb-0 inline-block">
                    <li class="inline breadcrumb-item text-[15px] font-semibold duration-500 ease-in-out text-white/50 hover:text-white">
                        <router-link to="/">Giglink</router-link>
                    </li>
                    <li class="inline breadcrumb-item text-[15px] font-semibold duration-500 ease-in-out text-white" aria-current="page">Blogs</li>
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
        <section class="relative md:py-24 py-16">
            <div class="container">
                <blogs :blog=true />
                <pagination />
            </div>
        </section>

        <switcher />

        <footers />
    </div>
</template>

<script setup>
import navbar from '@/components/navbar/navbar.vue';
import blogs from '@/components/blog/latest-blog.vue';
import pagination from '@/components/pagination.vue';
import switcher from '@/components/switcher.vue';
import footers from '@/components/footer/footer.vue'

</script>

<style lang="scss" scoped></style>