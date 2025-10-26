<template>
    <section class="relative md:py-24 py-16">
        <div class="container">
            <div>
                <h3 class="text-2xl font-bold mb-6 text-slate-800 dark:text-slate-100">Daftar Teknisi Remote</h3>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    <div
                        v-for="tech in teknisiList"
                        :key="tech.id"
                        class="flex flex-col sm:flex-row justify-between items-center sm:items-center bg-white/80 dark:bg-slate-900/80 rounded-2xl shadow-lg p-4 sm:p-6 lg:p-8 mb-6 border border-violet-200 dark:border-violet-700 backdrop-blur-md hover:scale-[1.03] hover:shadow-2xl transition-all duration-300 overflow-hidden relative w-full gap-4"
                        style="min-width:0; max-width:100%;"
                    >
                        <div class="absolute top-0 left-0 bg-gradient-to-r from-violet-500 to-blue-400 text-white text-xs font-bold px-3 py-1 rounded-br-xl shadow z-10">Remote Service</div>
                        <div class="flex items-center gap-4">
                            <div class="relative flex-shrink-0">
                                <img :src="tech.avatar" class="w-14 h-14 sm:w-20 sm:h-20 lg:w-24 lg:h-24 rounded-xl object-cover border-4 border-violet-300 shadow-lg" />
                                <span :class="tech.online ? 'bg-green-500' : 'bg-slate-400'" class="absolute bottom-1 right-1 w-4 h-4 rounded-full border-2 border-white flex items-center justify-center">
                                    <i class="mdi mdi-check-circle text-white text-xs" v-if="tech.online"></i>
                                    <i class="mdi mdi-minus-circle text-white text-xs" v-else></i>
                                </span>
                            </div>
                            <div class="flex-1 w-full">
                                <h4 class="font-bold text-base sm:text-lg lg:text-xl text-slate-800 dark:text-white flex items-center gap-2">
                                    {{ tech.name }}
                                    <span v-if="tech.online" class="px-2 py-0.5 rounded-full bg-green-100 text-green-700 text-xs font-bold ml-2">Online</span>
                                    <span v-else class="px-2 py-0.5 rounded-full bg-slate-200 text-slate-500 text-xs font-bold ml-2">Offline</span>
                                </h4>
                                <div class="flex flex-wrap gap-1 mt-1">
                                    <span
                                        v-for="(service, i) in tech.services"
                                        :key="i"
                                        class="text-xs bg-violet-100 text-violet-700 px-2 py-0.5 rounded-full font-semibold shadow"
                                    >
                                        <i class="mdi mdi-wrench text-violet-400 mr-1"></i>{{ service }}
                                    </span>
                                </div>
                            </div>
                        </div>
                        <div class="flex flex-col items-end sm:items-start gap-2 text-sm text-right sm:text-left mt-3 sm:mt-0">
                            <div class="flex flex-col items-center sm:items-start gap-2 text-center sm:text-left mt-3 sm:mt-0 w-full">
                                <p class="text-violet-600 dark:text-white font-bold text-sm sm:text-base lg:text-lg">{{ tech.price }}</p>
                                <p class="text-slate-500 dark:text-white text-xs sm:text-sm lg:text-base">{{ tech.duration }}</p>
                                <button @click="showDetail(tech)" type="button" class="mt-2 px-4 py-1 rounded-lg bg-violet-600 text-white hover:bg-violet-700 transition text-xs sm:text-sm font-semibold">Informasi Detail</button>
                            </div>
                        </div>
                    </div>
                    <pagination />
                </div>
            </div>
        </div>

                <dialog
                    v-if="selectedTech"
                    class="fixed inset-0 bg-black/50 flex items-center justify-center z-50"
                >
                    <div
                        class="bg-white dark:bg-slate-900 rounded-xl p-6 w-full max-w-lg relative shadow-xl"
                    >
                        <button
                            class="absolute top-3 right-3 text-slate-400 hover:text-red-500"
                            @click="selectedTech = null"
                        >
                            <i class="mdi mdi-close text-xl"></i>
                        </button>

                        <div class="flex items-center gap-4 mb-4">
                            <img :src="selectedTech.avatar" class="w-20 h-20 rounded-full object-cover" />
                            <div>
                                <h3 class="text-xl font-semibold text-slate-800 dark:text-white">
                                    {{ selectedTech.name }}
                                </h3>
                                <p class="text-slate-500">{{ selectedTech.specialization }}</p>
                                <span
                                    :class="selectedTech.online ? 'text-green-500' : 'text-slate-400'"
                                    class="text-sm font-medium"
                                >
                                    ● {{ selectedTech.online ? 'Online' : 'Offline' }}
                                </span>
                            </div>
                        </div>

                        <div class="space-y-2 text-slate-600 dark:text-slate-300">
                            <p><i class="mdi mdi-currency-usd"></i> <strong>Estimasi Biaya:</strong> {{ selectedTech.price }}</p>
                            <p><i class="mdi mdi-timer-outline"></i> <strong>Proses Pengerjaan:</strong> {{ selectedTech.duration }}</p>
                            <p><i class="mdi mdi-wrench-outline"></i> <strong>Layanan Remote:</strong></p>
                            <ul class="list-disc list-inside pl-4">
                                <li v-for="(srv, i) in selectedTech.services" :key="i">{{ srv }}</li>
                            </ul>
                            <p><i class="mdi mdi-laptop"></i> <strong>Tools:</strong> {{ selectedTech.tools }}</p>
                        </div>

                        <button
                            class="mt-6 w-full bg-violet-600 text-white py-2 rounded-lg hover:bg-violet-700 transition"
                        >
                            <i class="mdi mdi-chat-outline"></i> Chat Sekarang
                        </button>
                    </div>
                </dialog>
    </section>
</template>

<script>
import { useWorkshopStore } from '@/stores/storeWorkshop.ts'


export default {
    props: {
        discover: {
            type: Boolean,
            required: true
        },
        items: {
            type: Boolean,
            required: true
        },
        moreitem: {
            type: Boolean,
            required: true
        },
        explore: {
            type: Boolean,
            required: true
        },
    },
name: "ExploreOne",
data() {
    return {
        setProductData: [],
        teknisiList: [
            {
                id: 1,
                name: "Budi Santoso",
                specialization: "Software & Unlock Specialist",
                price: "Rp100K - Rp250K",
                duration: "30–60 menit",
                online: true,
                avatar: "https://randomuser.me/api/portraits/men/32.jpg",
                services: ["Bypass FRP", "Flashing Firmware", "Unlock SIM", "Data Recovery"],
                tools: "TeamViewer, AnyDesk",
            },
            {
                id: 2,
                name: "Rina Pratama",
                specialization: "IC & Touchscreen Technician",
                price: "Rp150K - Rp300K",
                duration: "1–2 jam",
                online: false,
                avatar: "https://randomuser.me/api/portraits/women/44.jpg",
                services: ["Flashing", "FRP Removal", "Touchscreen Repair"],
                tools: "AnyDesk",
            },
            {
                id: 3,
                name: "Ardi Nugroho",
                specialization: "Android Bootloader & FRP Expert",
                price: "Rp120K - Rp200K",
                duration: "20–40 menit",
                online: true,
                avatar: "https://randomuser.me/api/portraits/men/41.jpg",
                services: ["FRP Bypass", "Bootloader Unlock", "Google Account Remove"],
                tools: "TeamViewer",
            },
            {
                id: 4,
                name: "Siti Rahma",
                specialization: "Laptop & PC Specialist",
                price: "Rp200K - Rp350K",
                duration: "45–90 menit",
                online: false,
                avatar: "https://randomuser.me/api/portraits/women/65.jpg",
                services: ["Install Windows", "Virus Removal", "Data Backup"],
                tools: "AnyDesk, TeamViewer",
            },
        ],
        selectedTech: null,
        products: [
            {
                id: 1,
                mainimage: require('../assets/images/items/1.jpg'),
                image: require('../assets/images/avatar/1.jpg'),
                name: '@StreetBoy',
                title: 'Gensadsaduine Undjkbjbead #3902',
                location: 'Jakarta',
                rating: 5,
                skills: ['Desain Grafis', 'Fotografi'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
            {
                id: 2,
                mainimage: require('../assets/images/items/2.gif'),
                image: require('../assets/images/avatar/2.jpg'),
                name: '@CutieGirl',
                title: 'Windchime #768',
                location: 'Surabaya',
                rating: 4,
                skills: ['Web Development', 'UI/UX'],
                price: '3.5 ETH',
                date: 'August 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: true
            },
            {
                id: 3,
                mainimage: require('../assets/images/items/2.jpg'),
                image: require('../assets/images/items/3.gif'),
                name: '@ButterFly',
                title: 'Probably A Label #3277',
                location: 'Bandung',
                rating: 3,
                skills: ['Animasi', 'Ilustrasi'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
            {
                id: 4,
                mainimage: require('../assets/images/items/3.jpg'),
                image: require('../assets/images/avatar/3.jpg'),
                name: '@NorseQueen',
                title: 'Probably A Label #1711',
                location: 'Medan',
                rating: 5,
                skills: ['Digital Marketing', 'SEO'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
            {
                id: 5,
                mainimage: require('../assets/images/items/3.gif'),
                image: require('../assets/images/avatar/4.jpg'),
                name: '@BigBull',
                title: 'Shibuya Scramble Punks',
                location: 'Makassar',
                rating: 4,
                skills: ['Copywriting', 'Branding'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
            {
                id: 6,
                mainimage: require('../assets/images/items/4.jpg'),
                image: require('../assets/images/avatar/5.jpg'),
                name: '@Angel',
                title: 'Probably A Label #650',
                location: 'Yogyakarta',
                rating: 3,
                skills: ['Video Editing', 'Motion Graphic'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
            {
                id: 7,
                mainimage: require('../assets/images/items/5.jpg'),
                image: require('../assets/images/avatar/6.jpg'),
                name: '@CrazyAnyone',
                title: 'Looki#0147',
                location: 'Semarang',
                rating: 5,
                skills: ['Mobile App', 'UI/UX'],
                price: '3.5 ETH',
                date: 'January 29, 2026 6:0:0',
                highest: '3.55 ETH',
                showdate: true
            },
            {
                id: 8,
                mainimage: require('../assets/images/items/6.jpg'),
                image: require('../assets/images/items/5.gif'),
                name: '@Princess',
                title: 'Poob #285',
                location: 'Denpasar',
                rating: 4,
                skills: ['Desain Logo', 'Branding'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
            {
                id: 9,
                mainimage: require('../assets/images/items/8.jpg'),
                image: require('../assets/images/avatar/7.jpg'),
                name: '@LooserBad',
                title: 'Umber Arrow',
                location: 'Palembang',
                rating: 3,
                skills: ['Ilustrasi', 'Desain Grafis'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
            {
                id: 10,
                mainimage: require('../assets/images/items/4.gif'),
                image: require('../assets/images/items/5.gif'),
                name: '@Princess',
                title: 'Gloam Druid',
                location: 'Balikpapan',
                rating: 4,
                skills: ['Web Development', 'SEO'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
            {
                id: 11,
                mainimage: require('../assets/images/items/5.gif'),
                image: require('../assets/images/avatar/8.jpg'),
                name: '@PandaOne',
                title: 'Azuki #7421',
                location: 'Pontianak',
                rating: 5,
                skills: ['Animasi', 'Video Editing'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
            {
                id: 12,
                mainimage: require('../assets/images/items/9.jpg'),
                image: require('../assets/images/items/2.gif'),
                name: '@FunnyGuy',
                title: 'Wolf-Cult Vanguard',
                location: 'Padang',
                rating: 3,
                skills: ['Branding', 'Copywriting'],
                price: '3.5 ETH',
                date: 'January 29, 2025 6:0:0',
                highest: '3.55 ETH',
                showdate: false
            },
        ]
    }
},

mounted() {
    const workshopStore = useWorkshopStore()
    workshopStore.getWorkshop().then(() => {
        this.setProductData = workshopStore.workshops.map(item => ({
            ...item,
            remaining: this.tickTock(item.date),
        }))
    })

    this._interval = setInterval(() => {
        const workshopStore = useWorkshopStore()
        this.setProductData = workshopStore.workshops.map(item => ({
            ...item,
            remaining: this.tickTock(item.date),
        }))
    }, 1000)
},
beforeUnmount() {
    clearInterval(this._interval)
},
methods: {
    showDetail(tech) {
        this.selectedTech = tech;
    },
    tickTock(date) {
        let startDate = new Date(date);
        let currentDate = new Date();
        const diff = startDate.getTime() - currentDate.getTime();
        const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        const minutes = Math.floor((diff / (1000 * 60)) % 60);
        const seconds = Math.floor((diff / 1000) % 60);
        const days = Math.floor(diff / (1000 * 60 * 60 * 24));
        return { hours, minutes, seconds, days }
    },
    // remainingDays tidak perlu lagi, karena sudah dihandle di mounted & interval
}
}
</script>

<style lang="scss" scoped></style>