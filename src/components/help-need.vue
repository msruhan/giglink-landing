<template>
    <div class="container">
        <div class="grid grid-cols-1 pb-8 text-center">
            <h3 class="mb-4 md:text-3xl text-2xl md:leading-snug leading-snug font-semibold">Find The Help You Need</h3>

            <p class="text-slate-400 max-w-xl mx-auto">We are a huge marketplace dedicated to connecting great artists of all Giglink with their fans and unique token collectors!</p>
        </div><!--end grid-->

        <div class="grid grid-cols-1 lg:grid-cols-3 md:grid-cols-2 mt-6 gap-[30px]">
            <div v-for="item in datas" :key="item" class="text-center px-6 mt-6">
                <div class="size-20 bg-violet-600/5 text-violet-600 rounded-full text-3xl flex align-middle justify-center items-center shadow-sm dark:shadow-gray-800 mx-auto">
                    <i :class="item.icon"></i>
                </div>

                <div class="content mt-7">
                    <router-link :to="item.link" class="title h5 text-lg font-semibold hover:text-violet-600">{{item.name}}</router-link>
                    <p class="text-slate-400 mt-3">{{item.title}}</p>
                    
                    <div class="mt-5">
                        <router-link :to="item.link" class="btn btn-link text-violet-600 hover:text-violet-600 after:bg-violet-600 duration-500 ease-in-out">Read More <i class="uil uil-arrow-right"></i></router-link>
                    </div>
                </div>
            </div>

        </div><!--end grid-->
    </div><!--end container-->
</template>

<script setup>
const datas = [
    {
        icon: 'uil uil-question-circle',
        name: 'FAQs',
        title: 'The phrasal sequence of the is now so that many campaign and benefit',
        link: '/helpcenter-faqs'
    },
    {
        icon: 'uil uil-file-bookmark-alt',
        name: 'Guides / Support',
        title: 'The phrasal sequence of the is now so that many campaign and benefit',
        link: '/helpcenter-guides'
    },
    {
        icon: 'uil uil-cog',
        name: 'Support Request',
        title: 'The phrasal sequence of the is now so that many campaign and benefit',
        link: '/helpcenter-support'
    },
]
</script>

<style lang="scss" scoped>

</style>