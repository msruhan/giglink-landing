<template>
    <div class="container lg:mt-24 mt-16">
        <div class="grid grid-cols-1 pb-8 text-center">
            <h6 class="text-violet-600 font-medium mb-2">Our Minds</h6>
            <h3 class="mb-4 md:text-3xl text-2xl md:leading-snug leading-snug font-semibold">Management Team</h3>

            <p class="text-slate-400 max-w-xl mx-auto">We are a huge marketplace dedicated to connecting great artists of all Giglink with their fans and unique token collectors!</p>
        </div><!--end grid-->

        <div class="grid md:grid-cols-12 grid-cols-1 mt-8 gap-[30px]">
            <div v-for="item in datas" :key="item" class="lg:col-span-3 md:col-span-6">
                <div class="group text-center">
                    <div class="relative inline-block mx-auto size-52 rounded-full overflow-hidden">
                        <img :src="item.image" class="" alt="">
                        <div class="absolute inset-0 bg-gradient-to-b from-transparent to-black size-52 rounded-full opacity-0 group-hover:opacity-100 transition-all duration-500 ease-in-out"></div>

                        <ul class="list-none absolute start-0 end-0 -bottom-20 group-hover:bottom-5 transition-all duration-500 ease-in-out">
                            <li v-for="social in item.social" :key="social" class="inline me-1"><a href="" class="btn btn-icon btn-sm rounded-full border border-violet-600 bg-violet-600 hover:border-violet-600 hover:bg-violet-600 text-white"><i :data-feather="social" class="size-4"></i></a></li>
                        </ul><!--end icon-->
                    </div>

                    <div class="content mt-3">
                        <a href="" class="text-lg font-semibold hover:text-violet-600 transition-all duration-500 ease-in-out">{{item.name}}</a>
                        <p class="text-slate-400">{{item.position}}</p>
                    </div>
                </div>
            </div>
        </div><!--end grid-->
    </div><!--end container-->
</template>

<script setup>

const datas = [
    {
        image: require('../assets/images/client/04.jpg'),
        name: 'Jack John',
        position: 'Designer',
        social: ['facebook', 'instagram', 'linkedin']
    },
    {
        image: require('../assets/images/client/05.jpg'),
        name: 'Krista John',
        position: 'Designer',
        social: ['facebook', 'instagram', 'linkedin']
    },
    {
        image: require('../assets/images/client/06.jpg'),
        name: 'Roger Jackson',
        position: 'Designer',
        social: ['facebook', 'instagram', 'linkedin']
    },
    {
        image: require('../assets/images/client/07.jpg'),
        name: 'Johnny English',
        position: 'Designer',
        social: ['facebook', 'instagram', 'linkedin']
    },
]

</script>

<style lang="scss" scoped>

</style>