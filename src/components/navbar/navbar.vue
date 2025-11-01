<template>
  <!-- ✅ Floating Bottom Navbar (Mobile Only) -->
  <nav
    class="fixed bottom-2 left-1/2 -translate-x-1/2 bg-white dark:bg-slate-900 shadow-lg border border-gray-300 dark:border-gray-800 rounded-lg px-2 py-0.5 w-[92%] max-w-sm flex justify-around items-center z-50 sm:hidden backdrop-blur-md"
  >
    <ul class="flex justify-center items-center gap-14 w-full text-center font-inter">
      <li>
        <router-link
          to="/beranda"
          class="flex flex-col items-center text-gray-600 dark:text-gray-300 hover:text-emerald-600 transition"
        >
          <i class="uil uil-home text-base mb-[-2px]"></i>
          <span class="text-[10px] font-medium mt-[-2px]">Beranda</span>
        </router-link>
      </li>
      <li>
        <router-link
          to="/explore-workshop"
          class="flex flex-col items-center text-gray-600 dark:text-gray-300 hover:text-emerald-600 transition"
        >
          <i class="uil uil-wrench text-base mb-[-2px]"></i>
          <span class="text-[10px] font-medium mt-[-2px]">Workshop</span>
        </router-link>
      </li>
      <li>
        <router-link
          to="/explore-marketplace"
          class="flex flex-col items-center text-gray-600 dark:text-gray-300 hover:text-emerald-600 transition"
        >
          <i class="uil uil-shopping-cart text-base mb-[-2px]"></i>
          <span class="text-[10px] font-medium mt-[-2px]">Belanja</span>
        </router-link>
      </li>
      <li>
        <router-link
          to="/creator-profile-edit"
          class="flex flex-col items-center text-gray-600 dark:text-gray-300 hover:text-emerald-600 transition"
        >
          <i class="uil uil-user text-base mb-[-2px]"></i>
          <span class="text-[10px] font-medium mt-[-2px]">Akun</span>
        </router-link>
      </li>
    </ul>
  </nav>

  <!-- ✅ Mobile Header Section (Top, only visible on small screens) -->
  <div class="sm:hidden fixed top-0 left-0 w-full bg-white shadow-md z-40 px-5 pt-5 pb-3 rounded-b-2xl">
    <div class="flex items-center justify-between">
      <div class="flex items-center gap-3">
  <img src="@/assets/images/avatar/3.jpg" alt="Profile" class="w-9 h-9 rounded-full object-cover border border-gray-200" />
        <div>
          <p class="text-sm text-gray-500">Hello <i class="mdi mdi-hand-wave text-yellow-500 text-base align-middle"></i></p>
          <h2 class="text-lg font-semibold text-gray-900">Melviano</h2>
        </div>
      </div>
      <div class="flex items-center space-x-3">
        <button class="relative">
          <i class="uil uil-bell text-[22px] text-gray-700"></i>
          <span
            class="absolute -top-1 -right-1 bg-red-500 text-white text-[10px] rounded-full h-3.5 w-3.5 flex items-center justify-center"
            >2</span
          >
        </button>
        <button class="relative">
          <i class="uil uil-shopping-cart text-[22px] text-gray-700"></i>
          <span
            class="absolute -top-1 -right-1 bg-emerald-500 text-white text-[10px] rounded-full h-3.5 w-3.5 flex items-center justify-center"
            >3</span
          >
        </button>
      </div>
    </div>

    <!-- 🔍 Search Bar -->
    <div class="mt-4">
      <div class="relative">
        <i
          class="uil uil-search absolute left-3 top-1/2 transform -translate-y-1/2 text-gray-400 text-lg"
        ></i>
        <input
          type="text"
          placeholder="Search anything"
          class="w-full pl-10 pr-4 py-2.5 bg-[#f4f4f4] rounded-xl focus:outline-none focus:ring-2 focus:ring-emerald-500 text-sm"
        />
      </div>
    </div>
  </div>

  <!-- ✅ Desktop Navbar -->
  <nav
    class="fixed top-6 left-1/2 transform -translate-x-1/2 z-30 bg-white/90 backdrop-blur-lg border border-gray-200 shadow-sm px-12 py-3 rounded-full flex items-center justify-between w-[90%] max-w-5xl hidden sm:flex"
  >
    <!-- Logo -->
    <div class="flex items-center space-x-2">
      <router-link to="/" class="flex items-center">
        <span class="font-bold text-lg text-gray-800 ml-2">Giglink</span>
      </router-link>
    </div>

    <!-- Menu: Desktop -->
    <ul
      class="hidden md:flex space-x-8 text-gray-700 font-semibold font-geist"
    >
      <li>
        <router-link to="/beranda" class="hover:text-black transition">Beranda</router-link>
      </li>
      <li>
        <router-link to="/explore-marketplace" class="hover:text-black transition">Belanja</router-link>
      </li>
      <li>
        <router-link to="/explore-workshop" class="hover:text-black transition">Workshop</router-link>
      </li>
      <li>
        <router-link to="/explore-teknisi" class="hover:text-black transition">Jasa Remote</router-link>
      </li>
      <li>
        <router-link to="/explore-rekber" class="hover:text-black transition">Rekber</router-link>
      </li>
    </ul>

    <!-- Login Button -->
    <router-link
      to="/login"
      class="hidden md:flex items-center gap-2 bg-emerald-500 hover:bg-emerald-600 text-white font-semibold px-5 py-2 rounded-full shadow-sm hover:shadow-lg hover:scale-105 transition duration-200 font-geist"
    >
      Login
      <i class="uil uil-arrow-right"></i>
    </router-link>

    <!-- Mobile Menu Icon -->
    <button class="md:hidden text-gray-700 text-2xl" @click="toggle = !toggle">
      <i class="uil uil-bars"></i>
    </button>

    <!-- Mobile Dropdown -->
    <div
      v-if="toggle"
      class="fixed inset-0 z-50 bg-black bg-opacity-40 flex items-center justify-center md:hidden"
    >
      <div
        class="bg-white rounded-2xl p-6 w-11/12 max-w-sm mx-auto border border-gray-200 mt-80"
      >
        <ul class="space-y-4 text-gray-700 font-medium font-inter">
          <li><router-link to="/beranda" @click="toggle = false">Beranda</router-link></li>
          <li><router-link to="/explore-marketplace" @click="toggle = false">Belanja</router-link></li>
          <li><router-link to="/explore-lisensi" @click="toggle = false">Lisensi</router-link></li>
          <li><router-link to="/explore-workshop" @click="toggle = false">Workshop</router-link></li>
          <li><router-link to="/explore-teknisi" @click="toggle = false">Remote / Service Online</router-link></li>
          <li><router-link to="/explore-rekber" @click="toggle = false">Rekber</router-link></li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
import vClickOutside from 'v-click-outside'
import feather from 'feather-icons'

export default {
  directives: {
    clickOutside: vClickOutside.directive,
  },
  props: {
    navLight: { type: String, required: true },
    logoLight: { type: Boolean, required: true },
  },
  data() {
    return {
      toggle: false,
      activeIndex: '',
      isActive: false,
    }
  },
  mounted() {
    feather.replace()
  },
}
</script>

<style scoped>
@media (max-width: 640px) {
  body {
    padding-top: 110px; /* memberi ruang di atas untuk header mobile */
    padding-bottom: 80px; /* ruang untuk bottom navbar */
  }
}

.shadow-lg {
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.12);
}
</style>
