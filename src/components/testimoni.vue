<template>
    <div>
        <div class="container md:mt-24 mt-16">
            <div class="grid grid-cols-1 text-center mb-10">
                <h3 class="md:text-[30px] text-[26px] font-semibold">Testimoni Pengguna</h3>
            </div>
            <div class="grid md:grid-cols-3 sm:grid-cols-2 grid-cols-1 gap-6">
                <div v-for="(testi, idx) in testimonials" :key="idx" class="bg-white dark:bg-slate-900 rounded-lg shadow p-6 flex flex-col items-center">
                    <div class="text-slate-600 dark:text-slate-200 italic mb-4">"{{ testi.text }}"</div>
                    <div class="font-semibold text-violet-600">- {{ testi.name }}</div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            testimonials: [
                { text: 'Marketplace ini sangat membantu saya menemukan alat servis yang sulit dicari.', name: 'Budi, Jakarta' },
                { text: 'Komunitasnya aktif dan supportif, banyak ilmu baru setiap hari!', name: 'Siti, Surabaya' },
                { text: 'Transaksi rekber di sini aman dan cepat.', name: 'Andi, Bandung' },
                { text: 'Workshop-nya keren, narasumbernya berpengalaman.', name: 'Rina, Yogyakarta' },
                { text: 'Bisa diskusi dan jualan sekaligus, mantap!', name: 'Dewi, Medan' },
                { text: 'Banyak produk original dan harga bersaing.', name: 'Agus, Makassar' },
            ]
        }
    }
}
</script>

<style lang="scss" scoped></style>