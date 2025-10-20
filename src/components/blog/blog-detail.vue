<template>
    <div>
        <div class="container">
            <div class="md:flex justify-center">
                <div class="lg:w-3/5">
                    <h5 class="md:text-3xl text-2xl md:leading-snug leading-snug font-semibold">{{data?.title ? data?.title : "TOKEN2040: The Future of Crypto, Decrypted"}}</h5>
                    <p class="text-slate-400 text-lg mt-4">The NFT space has made unprecedented progress since we first launched Giglink in late 2021, as it hit several major milestones in the past…</p>

                    <div class="flex mt-5">
                        <span class="font-medium"><i class="uil uil-calendar-alt me-2"></i>20th October, 2022</span>
                        <span class="ms-3 font-medium"><i class="uil uil-clock me-2"></i>5 min read</span>
                    </div>

                    <div class="flex items-center mt-5">
                        <div class="relative inline-block">
                            <img src="../../assets/images/items/2.jpg " class="h-14 rounded-full" alt="">
                        </div>

                        <div class="ms-3">
                            <router-link to="/creator-profile" class="font-semibold block hover:text-violet-600">Michael Williams</router-link>
                            <span class="text-slate-400 text-sm block mt-1">{{data?.by ? data?.by : '@FunnyGuy'}}</span>
                        </div>
                    </div>
                </div>
            </div>

            <div class="md:flex justify-center mt-6">
                <div class="lg:w-full">
                    <div class="relative">
                        <img :src="data?.image ? data?.image : image" class="rounded-lg shadow-md dark:shadow-gray-800 w-full" alt="">
                        <div class="absolute bottom-2/4 translate-y-2/4 start-0 end-0 text-center">
                            <a @click="toggle" data-type="youtube" data-id="yba7hPeTSjk"
                                class="lightbox size-20 rounded-full shadow-lg dark:shadow-gray-800 inline-flex items-center justify-center bg-white dark:bg-slate-900 text-violet-600 cursor-pointer">
                                <i class="mdi mdi-play inline-flex items-center justify-center text-2xl"></i>
                            </a>
                        </div>
                    </div>
                </div>
            </div>

            <div class="md:flex justify-center mt-6">
                <div class="lg:w-3/5">
                    <p class="text-slate-400">However, as the space keeps expanding and people proceed to mint thousands of NFTs every day, an important question arises - how do we make sure that all that creative work remains accessible over time?</p>
                    <p class="text-slate-400 mt-4">Earlier this year, as NFTs began hitting the mainstream, the industry faced a major technical problem. As highlighted by some analysts, most of the JPEGs (or other file formats) that serve as the media basis for their respective NFTs weren't stored on the chain itself. Instead, NFTs often simply redirected to a URL where the corresponding media was hosted - in most cases, that was a separate domain that belonged to either the creator or the platform where that NFT was minted.</p>
                    <p class="text-slate-400 mt-4">But what happens when those domains go down? With that discovery, it became apparent that some NFTs have a single point of failure, which, in turn, could significantly impact their longevity and value.</p>
                    <p class="text-slate-400 mt-4">In light of that, numerous projects and organisations have begun working on a potential fix. In a recent Clubhouse session, we brought those pioneering protocols and projects - Protocol Labs (an open-source lab that is working on Filecoin, IPFS and libp2p), Async.art, Fleek and Arweave - together to have a constructive discussion about the future of NFT metadata. Here's a concise recap of the main ideas that were discussed there.</p>

                    <img src="../../assets/images/blog/05.jpg" class="rounded-lg mt-4" alt="">

                    <h5 class="text-lg font-semibold mt-4">What's an NFT?</h5>

                    <p class="text-slate-400 mt-4">This is the part that takes a bit of open-mindedness. An NFT is a unique digital token, with most using the ethereum blockchain to digitally record transactions. It's not a cryptocurrency like bitcoin or ether, because those are fungible -- exchangeable for another bitcoin or cash. NFTs are recorded in a digital ledger in the same way as cryptocurrency, so there's a listing of who owns each one.</p>
                    <p class="text-slate-400 mt-4">What makes an NFT unique is the digital asset tied to the token. This can be an image, video, tweet or piece of music that's uploaded to a marketplace, which creates the NFT to be sold.</p>
                </div>
            </div>
        </div><!--end container-->

            <!-- iframe start  -->
        <div :class="isActive ? 'fixed' : 'hidden'" class="bg-black/[0.9] top-0 left-0 bottom-0 w-[100%] h-[100%] z-999">
            <div class="h-[100%] flex items-center justify-center">
                <iframe src="https://www.youtube.com/embed/S_CGed6E610?feature=oembed" width="700" height="500"
                    frameborder="0"></iframe>
            </div><button class="text-slate-400 absolute top-[20px] right-[20px]">
                <svg stroke="currentColor" fill="none" stroke-width="2" viewBox="0 0 24 24" stroke-linecap="round"
                    stroke-linejoin="round" class="size-5" height="1em" width="1em" xmlns="http://www.w3.org/2000/svg"
                    @click="toggle">
                    <line x1="18" y1="6" x2="6" y2="18"></line>
                    <line x1="6" y1="6" x2="18" y2="18"></line>
                </svg>
            </button>
        </div>
        <!-- iframe end  -->

                <div class="container mt-10">
                    <div class="lg:w-3/5 mx-auto">
                        <h4 class="text-2xl font-bold mb-8">Diskusi & Komentar</h4>

                        <!-- Komentar utama -->
                        <div
                            v-for="comment in comments"
                            :key="comment.id"
                            class="mb-8 border-b border-slate-200 pb-6"
                        >
                            <div class="flex items-start gap-3">
                                <img
                                    :src="comment.avatar"
                                    class="rounded-full w-12 h-12 object-cover"
                                />
                                <div class="flex-1">
                                    <div class="font-semibold text-violet-700">
                                        {{ comment.name }}
                                    </div>
                                    <div class="text-xs text-slate-400 mb-1">
                                        {{ comment.time }}
                                    </div>
                                    <div
                                        class="text-base text-slate-700 dark:text-slate-200 mb-2"
                                    >
                                        {{ comment.text }}
                                    </div>
                                    <button
                                        @click="toggleReply(comment)"
                                        class="text-sm text-violet-600 hover:underline"
                                    >
                                        {{ comment.showReply ? 'Batal' : 'Balas' }}
                                    </button>

                                    <!-- Balasan -->
                                    <div
                                        v-for="reply in comment.replies"
                                        :key="reply.id"
                                        class="flex items-start gap-3 mt-4 ml-8"
                                    >
                                        <img
                                            :src="reply.avatar"
                                            class="rounded-full w-10 h-10 object-cover"
                                        />
                                        <div>
                                            <div class="font-semibold text-violet-700">
                                                {{ reply.name }}
                                            </div>
                                            <div class="text-xs text-slate-400 mb-1">
                                                {{ reply.time }}
                                            </div>
                                            <div
                                                class="text-base text-slate-700 dark:text-slate-200"
                                            >
                                                {{ reply.text }}
                                            </div>
                                        </div>
                                    </div>

                                    <!-- Form Balasan -->
                                    <div v-if="comment.showReply" class="mt-4 ml-8">
                                        <textarea
                                            v-model="comment.replyText"
                                            placeholder="Tulis balasan..."
                                            class="w-full rounded-lg border border-gray-300 px-3 py-2 mb-2"
                                        ></textarea>
                                        <button
                                            @click="addReply(comment)"
                                            class="btn bg-violet-600 text-white rounded-lg px-4 py-1 text-sm"
                                        >
                                            Kirim
                                        </button>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- Tambah komentar baru -->
                        <form @submit.prevent="addComment" class="mt-8 border-t border-slate-200 pt-6">
                            <h5 class="text-lg font-semibold mb-3">Tulis Komentar Baru</h5>
                            <div class="flex items-center gap-4 mb-2">
                                <img
                                    src="../../assets/images/avatar/6.jpg"
                                    class="rounded-full w-12 h-12 object-cover"
                                />
                                <input
                                    v-model="newComment.name"
                                    type="text"
                                    placeholder="Nama Anda"
                                    class="form-input w-1/3 rounded-xl border border-gray-300 px-3 py-2"
                                    required
                                />
                            </div>
                            <textarea
                                v-model="newComment.text"
                                placeholder="Tulis komentar..."
                                class="form-input w-full rounded-xl border border-gray-300 px-3 py-2 mb-2"
                                required
                            ></textarea>
                            <button
                                type="submit"
                                class="btn bg-violet-600 text-white rounded-xl px-6 py-2 font-semibold"
                            >
                                Kirim Komentar
                            </button>
                        </form>
                    </div>
                </div>
    </div>
</template>

<script setup>
import { ref, reactive, onMounted } from "vue";
import { useRoute } from 'vue-router';
import image from '../../assets/images/blog/single.jpg'

// ✅ Data dummy komentar
const comments = ref([
    {
        id: 1,
        name: "Rizal Pratama",
        avatar: require("../../assets/images/avatar/6.jpg"),
        text: "Artikel ini sangat bermanfaat, terima kasih!",
        time: "20 Okt 2025, 10:15",
        showReply: false,
        replyText: "",
        replies: [
            {
                id: 11,
                name: "Dewi Lestari",
                avatar: require("../../assets/images/avatar/7.jpg"),
                text: "Setuju banget Rizal, saya juga suka bagian penjelasan NFT-nya!",
                time: "20 Okt 2025, 11:45",
            },
        ],
    },
    {
        id: 2,
        name: "Dewi Lestari",
        avatar: require("../../assets/images/avatar/7.jpg"),
        text: "NFT memang masa depan digital!",
        time: "20 Okt 2025, 11:02",
        showReply: false,
        replyText: "",
        replies: [],
    },
]);

// ✅ Komentar baru
const newComment = reactive({
    name: "",
    text: "",
});

// ✅ Tambah komentar baru
function addComment() {
    if (!newComment.name || !newComment.text) return;

    comments.value.push({
        id: Date.now(),
        name: newComment.name,
        avatar: require("../../assets/images/avatar/6.jpg"),
        text: newComment.text,
        time: new Date().toLocaleString("id-ID", {
            day: "2-digit",
            month: "short",
            year: "numeric",
            hour: "2-digit",
            minute: "2-digit",
        }),
        showReply: false,
        replyText: "",
        replies: [],
    });

    newComment.name = "";
    newComment.text = "";
}

// ✅ Toggle form balasan
function toggleReply(comment) {
    comment.showReply = !comment.showReply;
}

// ✅ Tambah balasan ke komentar tertentu
function addReply(comment) {
    if (!comment.replyText) return;

    comment.replies.push({
        id: Date.now(),
        name: "Anda",
        avatar: require("../../assets/images/avatar/6.jpg"),
        text: comment.replyText,
        time: new Date().toLocaleString("id-ID", {
            day: "2-digit",
            month: "short",
            year: "numeric",
            hour: "2-digit",
            minute: "2-digit",
        }),
    });

    comment.replyText = "";
    comment.showReply = false;
}
const route = useRoute();
const id = ref('')
const data = ref('')
const isActive = ref(false)

const datas = ref([
{
        id: 1,
        image: require('../../assets/images/blog/01.jpg'),
        category: 'Arts',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'Mindfulness Activities for Kids & Toddlers with NFT',
        by: '@StreetBoy'
    },
    {
        id: 2,
        image: require('../../assets/images/blog/02.jpg'),
        category: 'Illustration',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'Save Thousands Of Lives Through This NFT',
        by: '@CutieGirl'
    },
    {
        id: 3,
        image: require('../../assets/images/blog/03.jpg'),
        category: 'Music',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'A place where technology meets craftsmanship',
        by: '@ButterFly'
    },
    {
        id: 4,
        image: require('../../assets/images/blog/04.jpg'),
        category: 'Video',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'NFT Market - A Compact Trike with the Big Benefits',
        by: '@NorseQueen'
    },
    {
        id: 5,
        image: require('../../assets/images/blog/05.jpg'),
        category: 'Games',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'Honoring Black History Month with Toddlers',
        by: '@BigBull'
    },
    {
        id: 6,
        image: require('../../assets/images/blog/06.jpg'),
        category: 'Memes',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'Setting Intentions Instead of Resolutions for 2021',
        by: '@Angel'
    },
    {
        id: 7,
        image: require('../../assets/images/blog/07.jpg'),
        category: 'GIFs',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'Clever Ways to Purchase Extraordinart Items',
        by: '@CrazyAnyone'
    },
    {
        id: 8,
        image: require('../../assets/images/blog/08.jpg'),
        category: 'Video',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'How to Save Money on Baby Essentials for NFT',
        by: '@Princess'
    },
    {
        id: 9,
        image: require('../../assets/images/blog/09.jpg'),
        category: 'Music',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'Liki Trike - A Compact Trike with the Big Benefits',
        by: '@LooserBad'
    },
    {
        id: 10,
        image: require('../../assets/images/blog/10.jpg'),
        category: 'Tech',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'NFT Market - A Compact the Big Benefits',
        by: '@Princess'
    },
    {
        id: 11,
        image: require('../../assets/images/blog/11.jpg'),
        category: 'Arts',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'Behind the Scenes of the creabik App',
        by: '@PandaOne'
    },
    {
        id: 12,
        image: require('../../assets/images/blog/12.jpg'),
        category: 'GIFs',
        date: '20th October, 2022',
        time: '5 min read',
        title: 'Meet fennouni, Product Designer at GitHub',
        by: '@FunnyGuy'
    },
])

function toggle(){
    isActive.value = !isActive.value
}

onMounted(() => {
    id.value = route.params.id
    data.value = datas.value.find((item) => item.id === parseInt(id.value))
})
</script>

<style lang="scss" scoped></style>