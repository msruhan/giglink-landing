<template>
  <!-- Bottom Navbar for Mobile -->
  <nav
    class="fixed bottom-0 left-0 right-0 bg-white dark:bg-slate-900 shadow-t p-2 border-t border-gray-200 dark:border-gray-800 sm:hidden z-50"
  >
    <ul class="flex justify-around items-center text-center">
      <li>
        <router-link to="/beranda" class="flex flex-col items-center text-gray-600 dark:text-gray-300">
          <i class="uil uil-home text-xl"></i>
          <span class="text-xs">Beranda</span>
        </router-link>
      </li>
      <li>
        <router-link to="/explore-workshop" class="flex flex-col items-center text-gray-600 dark:text-gray-300">
          <i class="uil uil-wrench text-xl"></i>
          <span class="text-xs">Workshop</span>
        </router-link>
      </li>
      <li>
        <router-link to="/explore-marketplace" class="flex flex-col items-center text-gray-600 dark:text-gray-300">
          <i class="uil uil-shopping-bag text-xl"></i>
          <span class="text-xs">Belanja</span>
        </router-link>
      </li>
      <li>
        <router-link to="/blogs" class="flex flex-col items-center text-gray-600 dark:text-gray-300">
          <i class="uil uil-chat text-xl"></i>
          <span class="text-xs">Blog</span>
        </router-link>
      </li>
      <li>
        <router-link to="/creator-profile-edit" class="flex flex-col items-center text-gray-600 dark:text-gray-300">
          <i class="uil uil-user text-xl"></i>
          <span class="text-xs">Akun</span>
        </router-link>
      </li>
    </ul>
  </nav>
  <nav class="fixed top-6 left-1/2 transform -translate-x-1/2 z-50 bg-white/90 backdrop-blur-md border border-gray-100 shadow-sm px-8 py-3 rounded-full flex items-center justify-between w-[90%] max-w-5xl">
    <!-- Logo -->
    <div class="flex items-center space-x-2">
      <router-link to="/" class="flex items-center">
        <!-- <div class="p-2 rounded-full bg-white">
          <img src="../../assets/images/logo-icon-28.png" alt="Logo" class="w-8 h-8" />
        </div> -->
        <span class="font-bold text-lg text-gray-800 ml-2">Giglink</span>
      </router-link>
    </div>

    <!-- Menu: Desktop -->
    <ul class="hidden md:flex space-x-8 text-gray-700 font-medium">
      <li><router-link to="/beranda" class="hover:text-black transition">Beranda</router-link></li>
      <li class="relative group">
        <span class="hover:text-black transition cursor-default">Belanja</span>
        <ul class="absolute left-0 top-full mt-2 bg-white border rounded-lg shadow-lg py-2 w-40 hidden group-hover:block">
          <li><router-link to="/explore-marketplace" class="block px-4 py-2 hover:bg-gray-100">Barang</router-link></li>
          <li><router-link to="/explore-lisensi" class="block px-4 py-2 hover:bg-gray-100">Lisensi</router-link></li>
        </ul>
      </li>
      <li><router-link to="/explore-workshop" class="hover:text-black transition">Workshop</router-link></li>
      <li class="relative group">
        <span class="hover:text-black transition cursor-default">Jasa</span>
        <ul class="absolute left-0 top-full mt-2 bg-white border rounded-lg shadow-lg py-2 w-56 hidden group-hover:block">
          <li><router-link to="/explore-teknisi" class="block px-4 py-2 hover:bg-gray-100">Remote / Service Online</router-link></li>
          <li><router-link to="/explore-rekber" class="block px-4 py-2 hover:bg-gray-100">Rekber</router-link></li>
        </ul>
      </li>
      <li class="relative group">
        <span class="hover:text-black transition cursor-default">Pages</span>
        <ul class="absolute left-0 top-full mt-2 bg-white border rounded-lg shadow-lg py-2 w-56 hidden group-hover:block">
          <li><router-link to="/aboutus" class="block px-4 py-2 hover:bg-gray-100">About Us</router-link></li>
          <li><router-link to="/creators" class="block px-4 py-2 hover:bg-gray-100">Creators</router-link></li>
          <li><router-link to="/creator-profile" class="block px-4 py-2 hover:bg-gray-100">Creator Profile</router-link></li>
          <li><router-link to="/creator-profile-edit" class="block px-4 py-2 hover:bg-gray-100">Profile Edit</router-link></li>
          <li><router-link to="/become-creator" class="block px-4 py-2 hover:bg-gray-100">Become Creator</router-link></li>
          <li><router-link to="/blogs" class="block px-4 py-2 hover:bg-gray-100">Blogs</router-link></li>
          <li><router-link to="/blog-detail" class="block px-4 py-2 hover:bg-gray-100">Blog Detail</router-link></li>
          <li><router-link to="/login" class="block px-4 py-2 hover:bg-gray-100">Login</router-link></li>
          <li><router-link to="/signup" class="block px-4 py-2 hover:bg-gray-100">Signup</router-link></li>
          <li><router-link to="/reset-password" class="block px-4 py-2 hover:bg-gray-100">Forgot Password</router-link></li>
          <li><router-link to="/lock-screen" class="block px-4 py-2 hover:bg-gray-100">Lock Screen</router-link></li>
          <li><router-link to="/comingsoon" class="block px-4 py-2 hover:bg-gray-100">Coming Soon</router-link></li>
          <li><router-link to="/maintenance" class="block px-4 py-2 hover:bg-gray-100">Maintenance</router-link></li>
          <li><router-link to="/error" class="block px-4 py-2 hover:bg-gray-100">404!</router-link></li>
          <li><router-link to="/thankyou" class="block px-4 py-2 hover:bg-gray-100">Thank you</router-link></li>
          <li><router-link to="/helpcenter-overview" class="block px-4 py-2 hover:bg-gray-100">Help Center Overview</router-link></li>
          <li><router-link to="/helpcenter-faqs" class="block px-4 py-2 hover:bg-gray-100">Help Center FAQs</router-link></li>
          <li><router-link to="/helpcenter-guides" class="block px-4 py-2 hover:bg-gray-100">Help Center Guides</router-link></li>
          <li><router-link to="/helpcenter-support" class="block px-4 py-2 hover:bg-gray-100">Help Center Support</router-link></li>
          <li><router-link to="/terms" class="block px-4 py-2 hover:bg-gray-100">Terms Policy</router-link></li>
          <li><router-link to="/privacy" class="block px-4 py-2 hover:bg-gray-100">Privacy Policy</router-link></li>
          <li><router-link to="/upload-work" class="block px-4 py-2 hover:bg-gray-100">Upload Works</router-link></li>
          <li><router-link to="/contact" class="block px-4 py-2 hover:bg-gray-100">Contact</router-link></li>
        </ul>
      </li>
    </ul>

    <!-- Button: Desktop -->
    <router-link to="/upload-work" class="hidden md:flex items-center gap-2 bg-emerald-500 hover:bg-emerald-600 text-white font-semibold px-5 py-2 rounded-full shadow-sm hover:shadow-lg hover:scale-105 transition duration-200">
      Login
      <i class="uil uil-arrow-right"></i>
    </router-link>

    <!-- Mobile Menu Icon -->
    <button class="md:hidden text-gray-700 text-2xl" @click="toggle = !toggle">
      <i class="uil uil-bars"></i>
    </button>

    <!-- Mobile Menu -->
    <div v-if="toggle" class="fixed inset-0 z-50 bg-black bg-opacity-40 flex items-center justify-center md:hidden">
      <div class="bg-white rounded-2xl p-6 w-11/12 max-w-sm mx-auto border border-gray-200">
        <ul class="space-y-4 text-gray-700 font-medium">
          <li><router-link to="/beranda" @click="toggle = false">Beranda</router-link></li>
          <li><router-link to="/explore-marketplace" @click="toggle = false">Barang</router-link></li>
          <li><router-link to="/explore-lisensi" @click="toggle = false">Lisensi</router-link></li>
          <li><router-link to="/explore-workshop" @click="toggle = false">Workshop</router-link></li>
          <li><router-link to="/explore-teknisi" @click="toggle = false">Remote / Service Online</router-link></li>
          <li><router-link to="/explore-rekber" @click="toggle = false">Rekber</router-link></li>
          <li><router-link to="/aboutus" @click="toggle = false">About Us</router-link></li>
          <li><router-link to="/creators" @click="toggle = false">Creators</router-link></li>
          <li><router-link to="/creator-profile" @click="toggle = false">Creator Profile</router-link></li>
          <li><router-link to="/creator-profile-edit" @click="toggle = false">Profile Edit</router-link></li>
          <li><router-link to="/become-creator" @click="toggle = false">Become Creator</router-link></li>
          <li><router-link to="/blogs" @click="toggle = false">Blogs</router-link></li>
          <li><router-link to="/blog-detail" @click="toggle = false">Blog Detail</router-link></li>
          <li><router-link to="/login" @click="toggle = false">Login</router-link></li>
          <li><router-link to="/signup" @click="toggle = false">Signup</router-link></li>
          <li><router-link to="/reset-password" @click="toggle = false">Forgot Password</router-link></li>
          <li><router-link to="/lock-screen" @click="toggle = false">Lock Screen</router-link></li>
          <li><router-link to="/comingsoon" @click="toggle = false">Coming Soon</router-link></li>
          <li><router-link to="/maintenance" @click="toggle = false">Maintenance</router-link></li>
          <li><router-link to="/error" @click="toggle = false">404!</router-link></li>
          <li><router-link to="/thankyou" @click="toggle = false">Thank you</router-link></li>
          <li><router-link to="/helpcenter-overview" @click="toggle = false">Help Center Overview</router-link></li>
          <li><router-link to="/helpcenter-faqs" @click="toggle = false">Help Center FAQs</router-link></li>
          <li><router-link to="/helpcenter-guides" @click="toggle = false">Help Center Guides</router-link></li>
          <li><router-link to="/helpcenter-support" @click="toggle = false">Help Center Support</router-link></li>
          <li><router-link to="/terms" @click="toggle = false">Terms Policy</router-link></li>
          <li><router-link to="/privacy" @click="toggle = false">Privacy Policy</router-link></li>
          <li><router-link to="/upload-work" @click="toggle = false">Upload Works</router-link></li>
          <li><router-link to="/contact" @click="toggle = false">Contact</router-link></li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<style scoped>
nav {
  box-shadow: 0 2px 15px rgba(0, 0, 0, 0.05);
}
</style>
<script>
import vClickOutside from 'v-click-outside';
import feather from 'feather-icons';
// import VueMetamask from 'vue-metamask';
export default {
    directives: {
        clickOutside: vClickOutside.directive,
    },
    props: {
        navLight: {
            type: String,
            required: true
        },
        logoLight: {
            type: Boolean,
            required: true
        }
    },
    data() {
        return {
            toggle: false,
            activeIndex: '',
            menu: true,
            openMenu: '',
            dropdownOpen: false,
            metamask: null,
            isActive: false
        }
    },
    // components:{
    //     VueMetamask
    // },
    created() {
        this.activeIndex = window.location.pathname
    },
    mounted() {
        window.addEventListener('scroll', this.handleScroll);
        document.addEventListener('click', this.handleClickOutside);
        feather.replace();
        this.scrollToTop();
        // Always keep nav-sticky on mobile
        const navbar = document.getElementById("topnav");
        if (window.innerWidth < 640 && navbar) {
            navbar.classList.add("nav-sticky");
        }
    },
    unmounted() {
        window.removeEventListener('scroll', this.handleScroll);
        document.removeEventListener('click', this.handleClickOutside);
    },

    methods: {
        handler() {
            this.toggle = !this.toggle;
        },
        submenu(item) {
            this.menu = !this.menu
            this.openMenu = item
        },
        handleScroll() {
            const navbar = document.getElementById("topnav");
            if (!navbar) return;
            if (window.innerWidth < 640) {
                navbar.classList.add("nav-sticky");
                return;
            }
            if (
                document.body.scrollTop >= 50 ||
                document.documentElement.scrollTop >= 50
            ) {
                navbar.classList.add("nav-sticky");
            } else {
                navbar.classList.remove("nav-sticky");
            }
        },
    handleClickOutside(event) {
      if (this.$refs.dropdownToggle && !this.$refs.dropdownToggle.contains(event.target)) {
        this.dropdownOpen = false;
      }
    },

        scrollToTop() {
            window.scrollTo({ top: 0, behavior: "smooth" });
        },
        connect() {
            if (window.ethereum) {
                window.ethereum.enable().then(() => {
                }).catch((error) => {
                    console.error(error);
                });
            } else {
                this.toggles();
                // const metaMaskInstallLink = "https://metamask.io/download/";
                // window.open(metaMaskInstallLink, "_blank");
            }
        },

        toggles() {
            this.isActive = !this.isActive;
        }
    },

}

</script>
<style lang="scss" scoped>
.shadow-t {
    box-shadow: 0 -1px 4px rgba(0, 0, 0, 0.1);
}

.shadow {
    box-shadow: 0 1px 4px rgba(0,0,0,0.08);
}

@media (max-width: 640px) {
    body {
        padding-bottom: 70px; /* tinggi navbar bawah */
        padding-top: 56px; /* tinggi navbar atas */
    }
}

/* Tambah padding bawah agar konten tidak ketutup navbar */
@media (max-width: 640px) {
    body {
        padding-bottom: 70px; /* tinggi navbar bawah */
    }
}
</style>