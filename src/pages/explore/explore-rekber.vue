<template>
    <div>
        <span class="fixed blur-[200px] w-[600px] h-[600px] rounded-full top-1/2 start-1/2 ltr:-translate-x-1/2 rtl:translate-x-1/2 -translate-y-1/2 bg-gradient-to-tl from-red-600/20 to-violet-600/20 dark:from-red-600/40 dark:to-violet-600/40"></span>

        <navbar />

        <!-- Start Hero -->
        <section class="relative md:pt-48 pt-36 overflow-hidden">
            <div class="container">
                <div class="grid grid-cols-1 justify-center text-center mt-10">
                    <div class="relative">
                        <div class="relative mb-5">
                            <h1 class="font-bold lg:leading-snug leading-snug text-4xl lg:text-6xl">Layanan Rekening Bersama</h1>

                            <div class="overflow-hidden after:content-[''] after:absolute after:h-10 after:w-10 after:bg-violet-600/10 dark:after:bg-violet-600/30 after:-top-[50px] after:start-[30%] after:-z-1 after:rounded-lg after:animate-[spin_10s_linear_infinite]"></div>

                            <div
                                class="overflow-hidden after:content-[''] after:absolute after:h-10 after:w-10 after:bg-violet-600/20 dark:after:bg-violet-600/40 after:bottom-[0] after:end-[15%] after:-z-1 after:rounded-full after:animate-ping">
                            </div>
                        </div>
                        <p class="text-slate-400 dark:text-white/70 text-lg max-w-2xl mx-auto">Nikmati transaksi aman dan nyaman dengan Rekening Bersama. Dana akan disimpan oleh Giglink hingga barang atau jasa diterima sesuai kesepakatan, sehingga melindungi pembeli dan penjual dari risiko penipuan.</p>

                        <div class="mt-8">
                            <a href="#form-rekber" class="btn bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white rounded-full">Mulai Transaksi Rekber</a>
                        </div>
                    </div>
                </div>
            </div><!--end container-->

        </section><!--end section-->

        <!-- <section class="relative md:py-24 py-16">
            <div class="container">
                <div class="grid grid-cols-1 text-center">
                    <h3 class="md:text-[30px] text-[26px] font-semibold">Discover Items</h3>
                </div>
                <discover :moreitem=true />
            </div>
            <div class="container md:mt-24 mt-16">
                <div class="grid grid-cols-1 text-center">
                    <h3 class="md:text-[30px] text-[26px] font-semibold">Best Creators & Sellers</h3>
                </div>
                <creators />
            </div>
            <question />
            <getintouch />
        </section> -->
        <!-- End Hero -->

        <section class="relative md:py-24 py-16">
            <div class="container max-w-6xl mx-auto mb-12">
                <h3 class="md:text-[30px] text-[26px] font-semibold text-center mb-8">Formulir Rekening Bersama</h3>
                <form class="bg-white dark:bg-slate-900 rounded-xl shadow p-8 space-y-6">
                    <div>
                        <label class="block font-medium mb-1" for="nama">Nama</label>
                        <input id="nama" type="text" class="form-input w-full border border-gray-300 rounded-lg px-4 py-2 focus:border-violet-600 focus:ring-0 dark:bg-slate-800 dark:border-gray-700" placeholder="Nama lengkap" />
                    </div>
                    <div>
                        <label class="block font-medium mb-1" for="wa">Nomor Whatsapp</label>
                        <input id="wa" type="text" class="form-input w-full border border-gray-300 rounded-lg px-4 py-2 focus:border-violet-600 focus:ring-0 dark:bg-slate-800 dark:border-gray-700" placeholder="08xxxxxxxxxx" />
                    </div>
                    <div>
                        <label class="block font-medium mb-1" for="telegram">Username Telegram</label>
                        <input id="telegram" type="text" class="form-input w-full border border-gray-300 rounded-lg px-4 py-2 focus:border-violet-600 focus:ring-0 dark:bg-slate-800 dark:border-gray-700" placeholder="@username" />
                    </div>
                    <div>
                        <label class="block font-medium mb-1" for="email">Email</label>
                        <input id="email" type="email" class="form-input w-full border border-gray-300 rounded-lg px-4 py-2 focus:border-violet-600 focus:ring-0 dark:bg-slate-800 dark:border-gray-700" placeholder="email@domain.com" />
                    </div>
                    <div>
                        <label class="block font-medium mb-1" for="catatan">Catatan</label>
                        <textarea id="catatan" rows="3" class="form-input w-full border border-gray-300 rounded-lg px-4 py-2 focus:border-violet-600 focus:ring-0 dark:bg-slate-800 dark:border-gray-700" placeholder="Catatan tambahan (opsional)"></textarea>
                    </div>
                    <div class="flex items-start">
                        <input id="setuju" type="checkbox" class="form-checkbox rounded text-violet-600 focus:ring-0 mt-1" />
                        <label for="setuju" class="ms-2 text-sm text-gray-700 dark:text-gray-300">Saya setuju bahwa dana akan disimpan oleh Rekber hingga barang diterima.</label>
                    </div>
                    <button type="submit" class="w-full btn bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white rounded-full py-3 font-semibold text-lg">Submit</button>
                </form>
            </div>

        </section>

        <footers />
        <switcher />
    </div>
</template>

<script setup>
import navbar from '@/components/navbar/navbar.vue';
// import collection from '@/components/top-collection.vue';
// import discover from '@/components/discover-items.vue';
// import creators from '@/components/best-creators.vue';
// import question from '@/components/question.vue';
// import getintouch from '@/components/get-in-touch.vue';
import footers from '@/components/footer/footer.vue';
import switcher from '@/components/switcher.vue'

</script>

<style lang="scss" scoped></style>