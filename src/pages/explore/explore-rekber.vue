<template>
    <div>
        <span class="fixed blur-[200px] w-[600px] h-[600px] rounded-full top-1/2 start-1/2 ltr:-translate-x-1/2 rtl:translate-x-1/2 -translate-y-1/2 bg-gradient-to-tl from-red-600/20 to-violet-600/20 dark:from-red-600/40 dark:to-violet-600/40"></span>

        <navbar />

        <!-- Start Hero -->
        <!-- <section class="relative md:pt-48 pt-12 overflow-hidden bg-[#f4f4f4] text-[#1a1a1a] min-h-screen font-inter pb-0"> -->
            <section class="relative md:pt-32 pt-12 overflow-hidden bg-[#f4f4f4] text-[#1a1a1a] font-inter pb-20">
             <div class="container hidden sm:block">
                <div class="grid grid-cols-1 justify-center text-center mt-10">
                    <div class="relative">
                        <div class="relative mb-5">
                            <h1
                                class="text-5xl md:text-6xl font-extrabold tracking-tight text-gray-900 leading-tight font-inter"
                            >
                                <span class="text-gray-900">Layanan</span> <span class="text-emerald-500">Rekening Bersama.</span>
                            </h1>
                        </div>
                        <p class="text-[#555] text-lg max-w-xl mx-auto font-inter">Nikmati transaksi aman dan nyaman dengan Rekening Bersama. Dana akan disimpan oleh Giglink hingga barang atau jasa diterima sesuai kesepakatan, sehingga melindungi pembeli dan penjual dari risiko penipuan</p>
                    </div>
                </div>
            </div>

        </section>

        <section class="relative bg-[#f4f4f4] text-[#1a1a1a] font-inter pb-40">
            <div class="container max-w-6xl mx-auto">
                <h3 class="md:text-[30px] text-[26px] font-semibold text-center mb-8 text-slate-800 dark:text-slate-100 font-geist">Formulir Rekening Bersama</h3>
                <form class="bg-white dark:bg-slate-900 rounded-xl shadow p-8 space-y-6 border border-emerald-200 dark:border-emerald-700">
                    <div>
                        <label class="block font-medium mb-1 font-inter" for="nama">Nama</label>
                        <input id="nama" type="text" class="form-input w-full border border-gray-300 rounded-lg px-4 py-2 focus:border-emerald-500 focus:ring-0 dark:bg-slate-800 dark:border-gray-700 font-inter" placeholder="Nama lengkap" />
                    </div>
                    <div>
                        <label class="block font-medium mb-1 font-inter" for="wa">Nomor Whatsapp</label>
                        <input id="wa" type="text" class="form-input w-full border border-gray-300 rounded-lg px-4 py-2 focus:border-emerald-500 focus:ring-0 dark:bg-slate-800 dark:border-gray-700 font-inter" placeholder="08xxxxxxxxxx" />
                    </div>
                    <div>
                        <label class="block font-medium mb-1 font-inter" for="telegram">Username Telegram</label>
                        <input id="telegram" type="text" class="form-input w-full border border-gray-300 rounded-lg px-4 py-2 focus:border-emerald-500 focus:ring-0 dark:bg-slate-800 dark:border-gray-700 font-inter" placeholder="@username" />
                    </div>
                    <div>
                        <label class="block font-medium mb-1 font-inter" for="email">Email</label>
                        <input id="email" type="email" class="form-input w-full border border-gray-300 rounded-lg px-4 py-2 focus:border-emerald-500 focus:ring-0 dark:bg-slate-800 dark:border-gray-700 font-inter" placeholder="email@domain.com" />
                    </div>
                    <div>
                        <label class="block font-medium mb-1 font-inter" for="catatan">Catatan</label>
                        <textarea id="catatan" rows="3" class="form-input w-full border border-gray-300 rounded-lg px-4 py-2 focus:border-emerald-500 focus:ring-0 dark:bg-slate-800 dark:border-gray-700 font-inter" placeholder="Catatan tambahan (opsional)"></textarea>
                    </div>
                    <div class="flex items-start">
                        <input id="setuju" type="checkbox" class="form-checkbox rounded text-emerald-500 focus:ring-0 mt-1" />
                        <label for="setuju" class="ms-2 text-sm text-gray-700 dark:text-gray-300 font-inter">Saya setuju bahwa dana akan disimpan oleh Rekber hingga barang diterima.</label>
                    </div>
                    <button type="submit" class="w-full btn bg-emerald-500 hover:bg-emerald-600 border-emerald-500 hover:border-emerald-600 text-white rounded-full py-3 font-semibold text-lg font-geist shadow-md transition-all duration-200">Submit</button>
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

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap');

.font-inter {
  font-family: 'Inter', sans-serif;
}

.shadow-md {
  box-shadow: 0 6px 18px rgba(0, 0, 0, 0.05);
}

.ring-gray-100 {
  --tw-ring-color: rgba(0, 0, 0, 0.05);
}
</style>