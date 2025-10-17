<template>
        <div class="container lg:mt-24 mt-16 lg:pt-24 pt-16">
                <div class="absolute inset-0 opacity-25 dark:opacity-50 bg-[url('../../assets/images/map.png')] bg-no-repeat bg-center"></div>
                <div class="relative grid grid-cols-1 pb-8 text-center z-1">
                    <h3 class="mb-4 md:text-3xl text-2xl md:leading-snug leading-snug font-semibold text-black dark:text-white">Trusted by more than 20K users</h3>

                    <p class="text-slate-400 max-w-xl mx-auto">We are a huge marketplace dedicated to connecting great artists of all Giglink with their fans and unique token collectors!</p>
                </div><!--end grid-->

                <div class="relative grid md:grid-cols-3 grid-cols-1 items-center mt-8 gap-[30px] z-1">
                    <div class="counter-box text-center">
                        <h1 class="lg:text-5xl text-4xl font-semibold mb-2 flex justify-center">$<count-up class="counter-value" :end-val="40">3</count-up>M</h1>
                        <h5 class="counter-head text-lg font-medium text-slate-400">Trading volume</h5>
                    </div><!--end counter box-->
                    
                    <div class="counter-box text-center">
                        <h1 class="lg:text-5xl text-4xl font-semibold mb-2 flex justify-center"><count-up class="counter-value" :end-val="200">2</count-up>+</h1>
                        <h5 class="counter-head text-lg font-medium text-slate-400">NFTs created</h5>
                    </div><!--end counter box-->
                    
                    <div class="counter-box text-center">
                        <h1 class="lg:text-5xl text-4xl font-semibold mb-2 flex justify-center"><count-up class="counter-value" :end-val="235">0</count-up>K</h1>
                        <h5 class="counter-head text-lg font-medium text-slate-400">Total users</h5>
                    </div><!--end counter box-->
                </div>
            </div><!--end container-->
</template>

<script setup>
import CountUp from 'vue-countup-v3';

</script>

<style lang="scss" scoped>

</style>