<template>
    <!-- Start Navbar -->
    <nav id="topnav" class="defaultscroll is-sticky">
        <div class="container">
            <!-- Logo container-->
            <router-link v-if="logoLight" class="logo ps-0" to="/">
                <img src="../../assets/images/logo-icon-28.png" class="inline-block sm:hidden" alt="">
                <div class="sm:block hidden">
                    <span class="inline-block dark:hidden">
                        <img src="../../assets/images/logo-dark.png" class="l-dark h-7" alt="">
                        <img src="../../assets/images/logo-light.png" class="l-light h-7" alt="">
                    </span>
                    <img src="../../assets/images/logo-white.png" height="24" class="hidden dark:inline-block" alt="">
                </div>
            </router-link>

            <router-link v-else class="logo ps-0" to="/">
                <img src="../../assets/images/logo-icon-28.png" class="inline-block sm:hidden" alt="">
                <div class="sm:block hidden">
                    <img src="../../assets/images/logo-dark.png" class="inline-block dark:hidden h-7" alt="">
                    <img src="../../assets/images/logo-white.png" class="hidden dark:inline-block h-7" alt="">
                </div>
            </router-link>
            <!-- End Logo container-->


            <div class="menu-extras" @click="handler">
                <div class="menu-item">
                    <!-- Mobile menu toggle-->
                    <a class="navbar-toggle" id="isToggle" :class="toggle === false ? '' : 'open'">
                        <div class="lines">
                            <span></span>
                            <span></span>
                            <span></span>
                        </div>
                    </a>
                    <!-- End mobile menu toggle-->
                </div>
            </div>

            <!--Login button Start-->
            <ul class="buy-button list-none mb-0">
                <!-- <li class="sm:inline-block hidden mb-0"> -->
                <!-- <li class="inline-block mb-0 me-1">
                    <div class="form-icon relative">
                        <i class="uil uil-search text-lg absolute top-1/2 -translate-y-1/2 start-3"></i>
                        <input type="text" class="form-input sm:w-44 w-28 ps-10 py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-3xl outline-none border border-gray-200 focus:border-violet-600 dark:border-gray-800 dark:focus:border-violet-600 focus:ring-0 bg-white" name="s" id="searchItem" placeholder="Search...">
                    </div>
                </li> -->

                <!-- <li class="inline-block ps-1 mb-0 me-1">
                    <a @click="connect" href="#!" id="connectWallet" class="btn btn-icon rounded-full bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white"><i class="uil uil-wallet"></i></a>
                            <VueMetamask ref="metamask" :initConnect="false" />
                </li> -->

                <li class="dropdown inline-block relative ps-1">
                    <button ref="dropdownToggle" @click="dropdownOpen = !dropdownOpen"  class="dropdown-toggle btn btn-icon rounded-full bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white inline-flex" type="button">
                        <img src="../../assets/images/client/05.jpg" class="rounded-full" alt="">
                    </button>
                    <!-- Dropdown menu -->
                    <div class="dropdown-menu absolute end-0 m-0 mt-4 z-10 w-48 rounded-md overflow-hidden bg-white dark:bg-slate-900 shadow dark:shadow-gray-800"  v-show="dropdownOpen">
                        <div class="relative">
                            <div class="py-8 bg-gradient-to-tr from-violet-600 to-red-600"></div>
                            <div class="absolute px-4 -bottom-7 start-0">
                                <div class="flex items-end">
                                    <img src="../../assets/images/client/05.jpg" class="rounded-full size-10 shadow dark:shadow-gray-700" alt="">

                                    <span class="font-semibold text-[15px] ms-1">Jenny Jimenez</span>
                                </div>
                            </div>
                        </div>

                        <div class="mt-10 px-4">
                            <h5 class="font-semibold text-[15px]">Wallet:</h5>
                            <div class="flex items-center justify-between">
                                <span class="text-[13px] text-slate-400">qhut0...hfteh45</span>
                                <a href="" class="text-violet-600"><i class="uil uil-copy"></i></a>
                            </div>
                        </div>

                        <div class="mt-4 px-4">
                            <h5 class="text-[15px]">Balance: <span class="text-violet-600 font-semibold">0.00045ETH</span></h5>
                        </div>

                        <ul class="py-2 text-start">
                            <li>
                                <router-link to="/creator-profile" class="block text-[14px] font-semibold py-1.5 px-4 hover:text-violet-600"><i class="uil uil-user text-[16px] align-middle me-1"></i> Profile</router-link>
                            </li>
                            <li>
                                <router-link to="/creator-profile-edit" class="block text-[14px] font-semibold py-1.5 px-4 hover:text-violet-600"><i class="uil uil-setting text-[16px] align-middle me-1"></i>Settings</router-link>
                            </li>
                            <li class="border-t border-gray-100 dark:border-gray-800 my-2"></li>
                            <li>
                                <router-link to="/login" class="block text-[14px] font-semibold py-1.5 px-4 hover:text-violet-600"><i class="uil uil-sign-out-alt text-[16px] align-middle me-1"></i>Logout</router-link>
                            </li>
                        </ul>
                    </div>
                </li>
            </ul>
            <!--Login button End-->

            <div id="navigation" :class="toggle === false ? 'none' : 'block'">
                <!-- Navigation Menu-->
                <ul class="navigation-menu justify-end" :class="navLight">
                    <!-- <li class="has-submenu parent-menu-item" :class="['/home', '/', '/index-two', '/index-three', '/index-four', '/index-five'].includes(activeIndex) ? 'active' : ''"><router-link to="" @click="submenu(openMenu === '/home' ? '' : '/home')">Home </router-link><span class="menu-arrow"></span>
                        <ul class="submenu" :class="['/home', '/', '/index-two', '/index-three', '/index-four', '/index-five'].includes(openMenu) ? 'open' : ''">
                            <li :class="activeIndex === '/' ? 'active' : ''"><router-link to="/" class="sub-menu-item">Home One</router-link></li>
                            <li :class="activeIndex === '/index-two' ? 'active' : ''"><router-link to="/index-two" class="sub-menu-item">Home Two</router-link></li>
                            <li :class="activeIndex === '/index-three' ? 'active' : ''"><router-link to="/index-three" class="sub-menu-item">Home Three</router-link></li>
                            <li :class="activeIndex === '/index-four' ? 'active' : ''"><router-link to="/index-four" class="sub-menu-item">Home Four</router-link></li>
                            <li :class="activeIndex === '/index-five' ? 'active' : ''"><router-link to="/index-five" class="sub-menu-item">Home Five</router-link></li>
                        </ul>
                    </li> -->

                    <li :class="activeIndex === '/beranda' ? 'active' : ''">
                        <router-link to="/beranda" class="sub-menu-item">Beranda</router-link>
                    </li>

                        
                    <li class="has-submenu parent-menu-item" :class="activeIndex === '/explore-workshop' ? 'active' : ''">
                      <a href="#" class="sub-menu-item cursor-default select-none pointer-events-none text-gray-500">Belanja</a><span class="menu-arrow"></span>
                      <ul class="submenu">
                        <li :class="activeIndex === '/explore-marketplace' ? 'active' : ''">
                          <router-link to="/explore-marketplace" class="sub-menu-item">Barang</router-link>
                        </li>
                        <li :class="activeIndex === '/explore-lisensi' ? 'active' : ''">
                          <router-link to="/explore-lisensi" class="sub-menu-item">Lisensi</router-link>
                        </li>
                      </ul>
                    </li>

                    <li :class="activeIndex === '/explore-workshop' ? 'active' : ''">
                        <router-link to="/explore-workshop" class="sub-menu-item">Workshop</router-link>
                    </li>

                    
                    <li class="has-submenu parent-menu-item" :class="activeIndex === '/explore-workshop' ? 'active' : ''">
                      <a href="#" class="sub-menu-item cursor-default select-none pointer-events-none text-gray-500">Jasa</a><span class="menu-arrow"></span>
                        <ul class="submenu">
                          <li :class="activeIndex === '/explore-teknisi' ? 'active' : ''">
                            <router-link to="/explore-teknisi" class="sub-menu-item">Remote / Service Online</router-link>
                          </li>
                          <li :class="activeIndex === '/explore-rekber' ? 'active' : ''">
                            <router-link to="/explore-rekber" class="sub-menu-item">Rekber</router-link>
                          </li>
                        </ul>
                    </li>
<!-- 
                    <li class="has-submenu parent-parent-menu-item" :class="['/explore', '/explore-one', '/explore-two', '/explore-three', '/auction', '/item-detail', '/activity', '/collections', '/upload-work',].includes(activeIndex) ? 'active' : ''">
                        <router-link to="/" @click="submenu(openMenu === '/explore' ? '' : '/explore')">Explore </router-link><span class="menu-arrow"></span>
                        <ul class="submenu" :class="['/explore', '/explore-one', '/explore-two', '/explore-three', '/auction', '/item-detail', '/activity', '/collections', '/upload-work'].includes(openMenu) ? 'open' : ''">
                            <li :class="activeIndex === '/explore-one' ? 'active' : ''"><router-link to="/explore-one" class="sub-menu-item"> Explore One</router-link></li>
                            <li :class="activeIndex === '/explore-two' ? 'active' : ''"><router-link to="/explore-two" class="sub-menu-item"> Explore Two</router-link></li>
                            <li :class="activeIndex === '/explore-three' ? 'active' : ''"><router-link to="/explore-three" class="sub-menu-item"> Explore Three</router-link></li>
                            <li :class="activeIndex === '/auction' ? 'active' : ''"><router-link to="/auction" class="sub-menu-item">Live Auction</router-link></li>
                            <li :class="activeIndex === '/item-detail' ? 'active' : ''"><router-link to="/item-detail" class="sub-menu-item"> Item Detail</router-link></li>
                            <li :class="activeIndex === '/activity' ? 'active' : ''"><router-link to="/activity" class="sub-menu-item"> Activities</router-link></li>
                            <li :class="activeIndex === '/collections' ? 'active' : ''"><router-link to="/collections" class="sub-menu-item">Collections</router-link></li>
                        </ul>
                    </li> -->

                    <!-- <li :class="activeIndex === '/wallet' ? 'active' : ''"><router-link to="/wallet" class="sub-menu-item">Wallet</router-link></li> -->

                    <li class="has-submenu parent-parent-menu-item" :class="['/aboutus', '/pages', '/creator', '/creators', '/creator-profile', '/creator-profile-edit', '/become-creator', '/blog', '/blogs', '/blog-detail', '/authpages', '/login', '/signup', '/reset-password', '/lock-screen', '/special', '/comingsoon', '/maintenance', '/error', '/thankyou', '/helpcenter', '/helpcenter-overview', '/helpcenter-faqs', '/helpcenter-guides', '/helpcenter-support', '/terms', '/privacy'].includes(activeIndex) ? 'active' : ''">
                        <router-link to="" @click="submenu(openMenu === '/pages' ? '' : '/pages')">Pages </router-link><span class="menu-arrow"></span>
                        <ul class="submenu" :class="['/aboutus', '/pages', '/creator', '/creators', '/creator-profile', '/creator-profile-edit', '/become-creator', '/blog', '/authpages', '/special', '/helpcenter'].includes(openMenu) ? 'open' : ''">
                            <li :class="activeIndex === '/aboutus' ? 'active' : ''"><router-link to="/aboutus" class="sub-menu-item">About Us</router-link></li>
                            <li class="has-submenu parent-menu-item" :class="['/creator', '/creators', '/creator-profile', '/creator-profile-edit', '/become-creator'].includes(activeIndex) ? 'active' : ''">
                                <router-link to="" @click="submenu(openMenu === '/creator' ? '' : '/creator')"> Creator
                                    <span class="submenu-arrow"></span></router-link>
                                <ul class="submenu" :class="['/creator', '/creators', '/creator-profile', '/creator-profile-edit', '/become-creator'].includes(openMenu) ? 'open' : ''">
                                    <li :class="activeIndex === '/creators' ? 'active' : ''"><router-link to="/creators" class="sub-menu-item"> Creators</router-link></li>
                                    <li :class="activeIndex === '/creator-profile' ? 'active' : ''"><router-link to="/creator-profile" class="sub-menu-item"> Creator Profile</router-link></li>
                                    <li :class="activeIndex === '/creator-profile-edit' ? 'active' : ''"><router-link to="/creator-profile-edit" class="sub-menu-item"> Profile Edit</router-link></li>
                                    <li :class="activeIndex === '/become-creator' ? 'active' : ''"><router-link to="/become-creator" class="sub-menu-item"> Become Creator</router-link></li>
                                </ul>
                            </li>
                            <li class="has-submenu parent-menu-item" :class="['/blog', '/blogs', '/blog-detail'].includes(activeIndex) ? 'active' : ''">
                                <router-link to="" @click="submenu(openMenu === '/blog' ? '' : '/blog')"> Blog <span class="submenu-arrow"></span></router-link>
                                <ul class="submenu" :class="['/blog', '/blogs', '/blog-detail'].includes(openMenu) ? 'open' : ''">
                                    <li :class="activeIndex === '/blogs' ? 'active' : ''"><router-link to="/blogs" class="sub-menu-item"> Blogs</router-link></li>
                                    <li :class="activeIndex === '/blog-detail' ? 'active' : ''"><router-link to="/blog-detail" class="sub-menu-item"> Blog Detail</router-link></li>
                                </ul>
                            </li>
                            <li class="has-submenu parent-menu-item" :class="['/authpages', '/login', '/signup', '/reset-password', '/lock-screen'].includes(activeIndex) ? 'active' : ''">
                                <router-link to="" @click="submenu(openMenu === '/authpages' ? '' : '/authpages')"> Auth Pages <span class="submenu-arrow"></span></router-link>
                                <ul class="submenu" :class="['/authpages', '/login', '/signup', '/reset-password', '/lock-screen'].includes(openMenu) ? 'open' : ''">
                                    <li :class="activeIndex === '/login' ? 'active' : ''"><router-link to="/login" class="sub-menu-item"> Login</router-link></li>
                                    <li :class="activeIndex === '/signup' ? 'active' : ''"><router-link to="/signup" class="sub-menu-item"> Signup</router-link></li>
                                    <li :class="activeIndex === '/reset-password' ? 'active' : ''"><router-link to="/reset-password" class="sub-menu-item"> Forgot Password</router-link></li>
                                    <li :class="activeIndex === '/lock-screen' ? 'active' : ''"><router-link to="/lock-screen" class="sub-menu-item"> Lock Screen</router-link></li>
                                </ul>
                            </li>
                            <li class="has-submenu parent-menu-item" :class="['/special', '/comingsoon', '/maintenance', '/error', '/thankyou'].includes(openMenu) ? 'active' : ''">
                                <router-link to="" @click="submenu(openMenu === '/special' ? '' : '/special')"> Special</router-link><span class="submenu-arrow"></span>
                                <ul class="submenu" :class="['/special', '/comingsoon', '/maintenance', '/error', '/thankyou'].includes(openMenu) ? 'open' : ''">
                                    <li :class="activeIndex === '/comingsoon' ? 'active' : ''"><router-link to="/comingsoon" class="sub-menu-item"> Coming Soon</router-link></li>
                                    <li :class="activeIndex === '/maintenance' ? 'active' : ''"><router-link to="/maintenance" class="sub-menu-item"> Maintenance</router-link></li>
                                    <li :class="activeIndex === '/error' ? 'active' : ''"><router-link to="/error" class="sub-menu-item"> 404!</router-link></li>
                                    <li :class="activeIndex === '/thankyou' ? 'active' : ''"><router-link to="/thankyou" class="sub-menu-item"> Thank you</router-link></li>
                                </ul>
                            </li>
                            <li class="has-submenu parent-menu-item" :class="['/helpcenter', '/helpcenter-overview', '/helpcenter-faqs', '/helpcenter-guides', '/helpcenter-support'].includes(activeIndex) ? 'active' : ''">
                                <router-link to="" @click="submenu(openMenu === '/heplcenter' ? '' : '/helpcenter')">Help Center </router-link><span class="submenu-arrow"></span>
                                <ul class="submenu" :class="['/helpcenter', '/helpcenter-overview', '/helpcenter-faqs', '/helpcenter-guides', '/helpcenter-support'].includes(openMenu) ? 'open' : ''">
                                    <li :class="activeIndex === '/helpcenter-overview' ? 'active' : ''"><router-link to="/helpcenter-overview" class="sub-menu-item"> Overview</router-link></li>
                                    <li :class="activeIndex === '/helpcenter-faqs' ? 'active' : ''"><router-link to="/helpcenter-faqs" class="sub-menu-item"> FAQs</router-link></li>
                                    <li :class="activeIndex === '/helpcenter-guides' ? 'active' : ''"><router-link to="/helpcenter-guides" class="sub-menu-item"> Guides</router-link></li>
                                    <li :class="activeIndex === '/helpcenter-support' ? 'active' : ''"><router-link to="/helpcenter-support" class="sub-menu-item"> Support</router-link></li>
                                </ul>
                            </li>
                            <li :class="activeIndex === '/terms' ? 'active' : ''"><router-link to="/terms" class="sub-menu-item">Terms Policy</router-link></li>
                            <li :class="activeIndex === '/privacy' ? 'active' : ''"><router-link to="/privacy" class="sub-menu-item">Privacy Policy</router-link></li>
                            <li :class="activeIndex === '/upload-work' ? 'active' : ''"><router-link to="/upload-work" class="sub-menu-item">Upload Works</router-link></li>
                            <li :class="activeIndex === '/contact' ? 'active' : ''"><router-link to="/contact" class="sub-menu-item">Contact</router-link></li>
                        </ul>
                    </li>
                </ul><!--end navigation menu-->
            </div><!--end navigation-->
        </div><!--end container-->
    </nav><!--end header-->
    <!-- End Navbar -->

</template>

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
        this.scrollToTop()
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
            if (!this.$refs.dropdownToggle.contains(event.target)) {
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
<style lang="scss" scoped></style>