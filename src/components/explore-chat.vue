<template>
        <div class="container mx-auto py-8">
            <div class="flex flex-col lg:flex-row gap-8">
            <!-- Main Content -->
            <div class="flex-1">
                <!-- Profile Card -->
                <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6 flex flex-col md:flex-row gap-6 items-center">
                <img :src="imageSrc2" class="w-32 h-32 rounded-full object-cover border-4 border-violet-600 shadow" alt="Profile" />
                <div class="flex-1 text-center md:text-left">
                    <h2 class="text-2xl font-bold flex items-center justify-center md:justify-start gap-2">
                    Michael Stewartsd
                    <i class="mdi mdi-check-decagram text-emerald-600 text-xl"></i>
                    </h2>
                    <p class="text-slate-500 text-lg">UI UX Designer</p>
                    <div class="flex flex-wrap justify-center md:justify-start gap-4 mt-2 text-slate-400 text-sm">
                    <span class="flex items-center gap-1"><i class="mdi mdi-map-marker"></i> Los Angeles</span>
                    <span class="flex items-center gap-1"><i class="mdi mdi-calendar"></i> 22 September 2023</span>
                    <span class="flex items-center gap-1"><i class="mdi mdi-star"></i> 5.0, 245 Reviews</span>
                    </div>
                    <div class="flex flex-wrap gap-2 mt-4 justify-center md:justify-start">
                    <button class="btn btn-sm rounded-full bg-violet-600 hover:bg-violet-700 text-white"><i class="mdi mdi-plus"></i> Follow me</button>
                    <button class="btn btn-icon btn-sm rounded-full bg-violet-600 hover:bg-violet-700 text-white"><i class="mdi mdi-account-plus"></i></button>
                    <router-link to="/creator-profile-edit" class="btn btn-icon btn-sm rounded-full bg-violet-100 hover:bg-violet-600 text-violet-600 hover:text-white"><i class="mdi mdi-cog"></i></router-link>
                    </div>
                </div>
                </div>

                <div class="flex h-screen bg-gray-100 text-gray-900">
            <!-- Sidebar Kiri -->
            <aside class="w-1/4 border-r border-gray-300 bg-white flex flex-col">
            <div class="p-4 flex items-center justify-between border-b">
                <h2 class="text-lg font-semibold">Chats</h2>
                <button class="p-2 rounded-full hover:bg-gray-200">
                <i class="ri-add-line text-xl"></i>
                </button>
            </div>
            <div class="p-3">
                <input
                v-model="search"
                type="text"
                placeholder="Cari..."
                class="w-full p-2 rounded-lg bg-gray-100 focus:outline-none"
                />
            </div>
            <div class="flex-1 overflow-y-auto">
                <div
                v-for="chat in filteredChats"
                :key="chat.id"
                @click="selectChat(chat)"
                class="flex items-center p-3 hover:bg-gray-100 cursor-pointer"
                :class="selectedChat?.id === chat.id ? 'bg-gray-200' : ''"
                >
                <img
                    :src="chat.avatar"
                    class="w-10 h-10 rounded-full object-cover"
                    alt="avatar"
                />
                <div class="ml-3 flex-1">
                    <div class="flex justify-between">
                    <h3 class="font-semibold">{{ chat.name }}</h3>
                    <span class="text-xs text-gray-500">{{ chat.time }}</span>
                    </div>
                    <p class="text-sm text-gray-500 truncate">{{ chat.lastMessage }}</p>
                </div>
                </div>
            </div>
            </aside>
            <!-- Area Chat Tengah -->
            <main class="flex-1 flex flex-col">
            <div
                v-if="selectedChat"
                class="flex items-center justify-between p-4 border-b bg-white"
            >
                <div class="flex items-center space-x-3">
                <img
                    :src="selectedChat.avatar"
                    class="w-10 h-10 rounded-full object-cover"
                />
                <div>
                    <h3 class="font-semibold">{{ selectedChat.name }}</h3>
                    <p class="text-xs text-green-500">Online</p>
                </div>
                </div>
                <div class="flex space-x-4">
                <i class="ri-phone-line text-xl cursor-pointer"></i>
                <i class="ri-video-line text-xl cursor-pointer"></i>
                </div>
            </div>
            <div v-if="selectedChat" class="flex-1 overflow-y-auto p-4 space-y-3">
                <div
                v-for="(msg, i) in selectedChat.messages"
                :key="i"
                class="flex"
                :class="msg.from === 'me' ? 'justify-end' : 'justify-start'"
                >
                <div
                    class="max-w-xs p-3 rounded-2xl"
                    :class="msg.from === 'me' ? 'bg-blue-500 text-white' : 'bg-gray-200'"
                >
                    {{ msg.text }}
                </div>
                </div>
            </div>
            <div
                v-if="selectedChat"
                class="border-t p-3 flex items-center bg-white"
            >
                <input
                v-model="newMessage"
                @keyup.enter="sendMessage"
                type="text"
                placeholder="Ketik pesan..."
                class="flex-1 p-2 bg-gray-100 rounded-lg focus:outline-none"
                />
                <button
                @click="sendMessage"
                class="ml-3 p-2 rounded-full bg-blue-500 text-white hover:bg-blue-600"
                >
                <i class="ri-send-plane-2-line text-xl"></i>
                </button>
            </div>
            <div v-else class="flex-1 flex items-center justify-center text-gray-400">
                Pilih percakapan untuk mulai chat
            </div>
            </main>
            <!-- Panel Kanan (Info) -->
            <aside
            v-if="selectedChat"
            class="w-1/4 border-l border-gray-300 bg-white p-4 flex flex-col"
            >
            <div class="text-center">
                <img
                :src="selectedChat.avatar"
                class="w-24 h-24 rounded-full mx-auto mb-3"
                />
                <h3 class="text-lg font-semibold">{{ selectedChat.name }}</h3>
                <p class="text-sm text-gray-500">Last seen 5m ago</p>
            </div>
            <hr class="my-4" />
            <div class="flex-1">
                <h4 class="font-semibold mb-2">Media, Links & Docs</h4>
                <div class="text-sm text-gray-500">
                <p>Belum ada media.</p>
                </div>
            </div>
            </aside>
        </div>

             <!-- Sidebar -->
            <div class="w-full lg:w-80 flex-shrink-0 space-y-6">
                <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6">
                <h4 class="font-bold text-lg mb-2">Skills</h4>
                <div class="flex flex-wrap gap-2">
                    <span class="px-3 py-1 rounded-full bg-violet-100 text-violet-700 text-xs font-medium">After Effects</span>
                    <span class="px-3 py-1 rounded-full bg-violet-100 text-violet-700 text-xs font-medium">Illustrator</span>
                    <span class="px-3 py-1 rounded-full bg-violet-100 text-violet-700 text-xs font-medium">HTML</span>
                    <span class="px-3 py-1 rounded-full bg-violet-100 text-violet-700 text-xs font-medium">Whiteboard</span>
                    <span class="px-3 py-1 rounded-full bg-violet-100 text-violet-700 text-xs font-medium">Software Design</span>
                    <span class="px-3 py-1 rounded-full bg-violet-100 text-violet-700 text-xs font-medium">HTML5</span>
                    <span class="px-3 py-1 rounded-full bg-violet-100 text-violet-700 text-xs font-medium">Design Writing</span>
                    <span class="px-3 py-1 rounded-full bg-violet-100 text-violet-700 text-xs font-medium">Web design</span>
                </div>
                </div>
            </div>
                <!-- Description -->
              <div class="bg-white dark:bg-slate-900 rounded-xl shadow p-6 mt-6">
                <h3 class="text-xl font-bold mb-2">Description</h3>
                <p class="text-slate-500 mb-2">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
                <p class="text-slate-500">Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo.</p>
              </div>
            </div>
            </div>
        </div>
</template>

<script setup>
import images2 from '../assets/images/avatar/1.jpg'
// import { ref } from 'vue'
const imageSrc2 = ref(images2)
import { ref, computed } from "vue";


const search = ref("");
const newMessage = ref("");
const selectedChat = ref(null);

const chats = ref([
  {
    id: 1,
    name: "Rian Teknisi",
    avatar: "https://i.pravatar.cc/100?img=1",
    lastMessage: "Lagi ngerjain iPhone bypass nih...",
    time: "10:24",
    messages: [
      { from: "Rian", text: "Bro, firmware udah fix?" },
      { from: "me", text: "Udah, tinggal flashing aja." },
    ],
  },
  {
    id: 2,
    name: "Budi GSM",
    avatar: "https://i.pravatar.cc/100?img=5",
    lastMessage: "Makasih, tool bypass-nya mantap!",
    time: "09:41",
    messages: [
      { from: "Budi", text: "Makasih, tool bypass-nya mantap!" },
      { from: "me", text: "Siap, semoga membantu bro!" },
    ],
  },
]);

const filteredChats = computed(() =>
  chats.value.filter((c) =>
    c.name.toLowerCase().includes(search.value.toLowerCase())
  )
);

function selectChat(chat) {
  selectedChat.value = chat;
}

function sendMessage() {
  if (newMessage.value.trim() === "" || !selectedChat.value) return;
  selectedChat.value.messages.push({
    from: "me",
    text: newMessage.value,
  });
  newMessage.value = "";
}
</script>

<style lang="scss" scoped>
.btn {
  @apply px-4 py-2 rounded-full font-semibold shadow transition;
}
.btn-primary {
  @apply bg-violet-600 hover:bg-violet-700 text-white;
}

::-webkit-scrollbar {
  width: 5px;
}
::-webkit-scrollbar-thumb {
  background: #ccc;
  border-radius: 5px;
}

</style>