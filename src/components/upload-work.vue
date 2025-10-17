<template>
    <div class="grid md:grid-cols-12 gap-[30px]">
        <div class="lg:col-span-3 md:col-span-4">
            <div class="overflow-hidden rounded-md shadow dark:shadow-gray-800 sticky top-20">
                <div class="py-10 bg-[url('../../assets/images/blog/05.jpg')] bg-center bg-no-repeat"></div>

                <div class="relative text-center -mt-10 p-6 pt-0">
                    <img src="../assets/images/avatar/1.jpg" class="bg-white dark:bg-slate-900 size-20 rounded-full shadow-md dark:shadow-gray-800 mx-auto p-1" alt="">
                
                    <div class="mt-3">
                        <router-link to="/creator-profile" class="font-semibold block hover:text-violet-600">Steven Townsend</router-link>
                        <span class="text-slate-400 text-sm block mt-1">@StreetBoy</span>
                    </div>

                    <ul class="list-none sidebar-nav mb-0 mt-3" id="navmenu-nav">
                        <li :class="activeIndex === '/creator-profile' ? 'active' : ''" class="navbar-item account-menu text-[16px]">
                            <router-link to="/creator-profile" class="navbar-link text-slate-400 flex items-center py-2 rounded">
                                <span class="me-2 mb-0"><i class="uil uil-dashboard"></i></span>
                                <h6 class="mb-0 font-medium">Profile</h6>
                            </router-link>
                        </li>

                        <li :class="activeIndex === '/upload-work' ? 'active' : ''" class="navbar-item account-menu text-[16px]">
                            <router-link to="/upload-work" class="navbar-link text-slate-400 flex items-center py-2 rounded">
                                <span class="me-2 mb-0"><i class="uil uil-browser"></i></span>
                                <h6 class="mb-0 font-medium">Upload Work</h6>
                            </router-link>
                        </li>

                        <li :class="activeIndex === '/creator-profile-edit' ? 'active' : ''" class="navbar-item account-menu text-[16px]">
                            <router-link to="/creator-profile-edit" class="navbar-link text-slate-400 flex items-center py-2 rounded">
                                <span class="me-2 mb-0"><i class="uil uil-setting"></i></span>
                                <h6 class="mb-0 font-medium">Settings</h6>
                            </router-link>
                        </li>

                        <li :class="activeIndex === '/lock-screen' ? 'active' : ''" class="navbar-item account-menu text-[16px]">
                            <router-link to="/lock-screen" class="navbar-link text-slate-400 flex items-center py-2 rounded">
                                <span class="me-2 mb-0"><i class="uil uil-sign-in-alt"></i></span>
                                <h6 class="mb-0 font-medium">Logout</h6>
                            </router-link>
                        </li>
                    </ul>
                </div>
            </div>
        </div>

        <div class="lg:col-span-9 md:col-span-8">
            <div class="lg:flex p-6 bg-white dark:bg-slate-900 rounded-md shadow dark:shadow-gray-800">
                <div class="lg:w-1/3 md:w-full">
                    <p   class="font-semibold mb-6">Upload your ART here, Please click "Upload Image" Button.</p>
                    <div v-if="imageSrc === null ? 'hiiden' : ''" class="preview-box flex justify-center rounded-md shadow dark:shadow-gray-800 overflow-hidden bg-gray-50 dark:bg-slate-800 text-slate-400 p-2 text-center small">Supports JPG, PNG and MP4 videos. Max file size : 10MB.</div>
                    <div v-else class="preview-box flex justify-center rounded-md shadow dark:shadow-gray-800 overflow-hidden bg-gray-50 dark:bg-slate-800 text-slate-400 p-2 text-center small"><img class="preview-content" :src="imageSrc"></div>
                    <input type="file" id="input-file" name="input-file" accept="image/*" @change="loadFile" hidden>
                    <label class="btn-upload btn bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white rounded-full w-full mt-6 cursor-pointer" for="input-file">Upload Image</label>
                </div>

                <div class="lg:w-2/3 md:w-full mt-8 lg:mt-0 lg:ms-6">
                    <form>
                        <div class="grid grid-cols-12 gap-6">
                            <div class="col-span-12">
                                <label class="font-semibold">Art Title <span class="text-red-600">*</span></label>
                                <input name="name" id="name" type="text" class="form-input w-full text-[15px] py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-violet-600 dark:border-gray-800 dark:focus:border-violet-600 focus:ring-0 mt-2" placeholder="Title :">
                            </div><!--end col-->

                            <div class="col-span-12">
                                <label class="font-semibold"> Description : </label>
                                <textarea name="comments" id="comments" class="form-input w-full text-[15px] py-2 px-3 h-28 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-2xl outline-none border border-gray-200 focus:border-violet-600 dark:border-gray-800 dark:focus:border-violet-600 focus:ring-0 mt-2" placeholder="Description :"></textarea>
                            </div><!--end col-->

                            <div class="md:col-span-6 col-span-12">
                                <label class="font-semibold">Type :</label>
                                <select class="form-input w-full text-[15px] py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-violet-600 dark:border-gray-800 dark:focus:border-violet-600 focus:ring-0 mt-2">
                                    <option>GIFs</option>
                                    <option>Music</option>
                                    <option>Video</option>
                                    <option>Tech</option>
                                </select>
                            </div><!--end col-->

                            <div class="md:col-span-6 col-span-12">
                                <label class="font-semibold"> Rate : </label>
                                <input name="time" type="number" class="form-input w-full text-[15px] py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-violet-600 dark:border-gray-800 dark:focus:border-violet-600 focus:ring-0 mt-2" id="time" placeholder="0.004ETH">
                            </div><!--end col-->

                            <div class="col-span-12">
                                <h6 class="font-semibold text-lg">Auction :</h6>
                            </div>

                            <div class="md:col-span-6 col-span-12">
                                <label class="font-semibold"> Starting Date : </label>
                                <input name="date" type="text" class="form-input w-full text-[15px] py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-violet-600 dark:border-gray-800 dark:focus:border-violet-600 focus:ring-0 mt-2 start" placeholder="Select date :">
                            </div><!--end col-->

                            <div class="md:col-span-6 col-span-12">
                                <label class="font-semibold"> Expiration date : </label>
                                <input name="date" type="text" class="form-input w-full text-[15px] py-2 px-3 h-10 bg-transparent dark:bg-slate-900 dark:text-slate-200 rounded-full outline-none border border-gray-200 focus:border-violet-600 dark:border-gray-800 dark:focus:border-violet-600 focus:ring-0 mt-2 end" placeholder="Select date :">
                            </div><!--end col-->

                            <div class="col-span-12">
                                <button type="submit" class="btn bg-violet-600 hover:bg-violet-700 border-violet-600 hover:border-violet-700 text-white rounded-full">Create Item</button>
                            </div><!--end col-->
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const imageSrc = ref(null)
const image = ref('')
const activeIndex = computed(() => window.location.pathname);

function loadFile(event) {
    image.value = document.getElementById(event.target.name)
    imageSrc.value = URL.createObjectURL(event.target.files[0])
}
</script>

<style lang="scss" scoped>

</style>