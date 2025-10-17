<template>
   <div>
        <div class="grid grid-cols-1 text-center">
            <h3 class="mb-4 md:text-3xl text-2xl md:leading-snug leading-snug font-semibold">Giglink is a web3 destination.</h3>

            <p class="text-slate-400 max-w-xl mx-auto">We are a huge marketplace dedicated to connecting great artists of all Giglink with their fans and unique token collectors!</p>
        </div><!--end grid-->

        <div class="grid lg:grid-cols-3 md:grid-cols-2 grid-cols-1 mt-10 gap-[30px]">
            <!-- Content -->
            <div v-for="item in datas" :key="item" class="group relative lg:px-6 mt-4 transition duration-500 ease-in-out rounded-xl overflow-hidden text-center">
                <div class="relative overflow-hidden text-transparent -m-3">
                    <i data-feather="hexagon" class="size-28 fill-violet-600/5 mx-auto rotate-[30deg]"></i>
                    <div class="absolute top-2/4 -translate-y-2/4 start-0 end-0 mx-auto text-violet-600 rounded-xl transition duration-500 ease-in-out text-3xl flex align-middle justify-center items-center">
                        <i :class="item.icon"></i>
                    </div>
                </div>

                <div class="mt-6">
                    <a href="" class="text-lg h5 font-semibold transition duration-500 ease-in-out hover:text-violet-600">{{ item.name }}</a>
                    <p class="text-slate-400 transition duration-500 ease-in-out mt-3">{{item.title}}</p>
                </div>
            </div>
            <!-- Content -->
        </div><!--end grid-->
    </div>
</template>

<script setup>

const datas = [
    {
        icon: 'uil uil-sitemap',
        name: 'Marketplace',
        title: "If the distribution of letters and 'words' is random, the reader will not be distracted from making."
    },
    {
        icon: 'uil uil-layers',
        name: 'Toko / Workshop',
        title: "If the distribution of letters and 'words' is random, the reader will not be distracted from making."
    },
    {
        icon: 'uil uil-layers',
        name: 'Jasa Servis',
        title: "If the distribution of letters and 'words' is random, the reader will not be distracted from making."
    },
    {
        icon: 'uil uil-layers',
        name: 'Blog & Tutorial',
        title: "If the distribution of letters and 'words' is random, the reader will not be distracted from making."
    },
    {
        icon: 'uil uil-camera-plus',
        name: 'Rekber',
        title: "If the distribution of letters and 'words' is random, the reader will not be distracted from making."
    },
]

</script>

<style lang="scss" scoped></style>