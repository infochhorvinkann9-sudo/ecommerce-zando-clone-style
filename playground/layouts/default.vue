<!-- layouts/default.vue -->
<template>
    <div class="bg-white text-gray-900 antialiased relative min-h-screen flex flex-col font-['Montserrat',sans-serif]">

        <!-- ================= TOP NAVIGATION BAR ================= -->
        <header class="sticky top-0 z-40 bg-white border-b border-gray-200 shadow-sm">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 h-16 flex items-center justify-between gap-6">

                <!-- Left: Categories / Nav Links -->
                <nav class="hidden md:flex items-center space-x-7 text-[13px] font-[900] tracking-tight uppercase">
                    <NuxtLink to="/" class="text-black hover:text-red-600 transition" active-class="text-red-600">
                        WOMEN
                    </NuxtLink>
                    <NuxtLink to="/" class="text-black hover:text-red-600 transition" active-class="text-red-600">
                        MEN
                    </NuxtLink>
                    <NuxtLink to="/" class="text-[#ff4f93] hover:opacity-80 transition">
                        BEAUTY
                    </NuxtLink>
                    <NuxtLink to="/about" class="text-black hover:text-red-600 transition" active-class="text-red-600">
                        ABOUT
                    </NuxtLink>
                    <NuxtLink to="/contact" class="text-black hover:text-red-600 transition"
                        active-class="text-red-600">
                        CONTACT
                    </NuxtLink>
                </nav>

                <!-- Center: LUMORA. Logo -->
                <div class="flex-shrink-0">
                    <NuxtLink to="/"
                        class="text-3xl font-[900] tracking-tighter uppercase italic hover:opacity-90 transition inline-block scale-y-95 text-black">
                        LUMORA<span class="text-red-600">.</span>
                    </NuxtLink>
                </div>

                <!-- Right: Utility Actions & Auth -->
                <div class="flex items-center space-x-5">
                    <!-- Search Bar -->
                    <div class="relative hidden sm:block w-44 lg:w-52">
                        <i
                            class="fa-solid fa-magnifying-glass absolute left-3 top-1/2 -translate-y-1/2 text-gray-400 text-xs"></i>
                        <input type="text" placeholder="Search"
                            class="w-full bg-white border border-gray-300 rounded-md py-1.5 pl-8 pr-3 text-xs focus:outline-none focus:border-black transition placeholder:text-gray-400" />
                    </div>

                    <!-- Notification Icon -->
                    <button class="text-black hover:opacity-70 transition">
                        <i class="fa-regular fa-bell text-base"></i>
                    </button>

                    <!-- Wishlist Icon -->
                    <button class="text-black hover:opacity-70 transition">
                        <i class="fa-regular fa-heart text-base"></i>
                    </button>

                    <!-- Cart Icon -->
                    <button class="relative text-black hover:opacity-70 transition">
                        <i class="fa-solid fa-bag-shopping text-base"></i>
                        <span
                            class="absolute -top-1.5 -right-2 bg-red-600 text-white text-[9px] font-black rounded-full h-4 w-4 flex items-center justify-center">
                            0
                        </span>
                    </button>

                    <!-- LOGIN / REGISTER Triggers -->
                    <div
                        class="hidden lg:flex items-center space-x-2 text-[12px] font-[900] tracking-tight border-l pl-4 border-gray-200">
                        <button @click="openModal('login')"
                            class="text-black hover:text-red-600 uppercase transition focus:outline-none">
                            LOGIN
                        </button>
                        <span class="text-gray-400 font-normal">/</span>
                        <button @click="openModal('register')"
                            class="text-black hover:text-red-600 uppercase transition focus:outline-none">
                            REGISTER
                        </button>
                    </div>
                </div>

            </div>
        </header>

        <!-- ================= MAIN CONTENT SLOT ================= -->
        <div class="flex-grow">
            <slot />
        </div>

        <!-- ================= FOOTER ================= -->
        <footer class="max-w-7xl mx-auto px-4 sm:px-6 pt-16 pb-12 border-t border-gray-100 mt-16 w-full">
            <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-5 gap-8 text-xs">
                <div>
                    <h3 class="font-extrabold uppercase tracking-wider text-[13px] mb-4">LUMORA APP</h3>
                    <div class="w-24 h-24 p-1 border border-gray-200 rounded-md shadow-sm">
                        <img src="https://api.qrserver.com/v1/create-qr-code/?size=150x150&data=https://zandokh.com"
                            alt="QR Code" class="w-full h-full object-contain" />
                    </div>
                </div>

                <div>
                    <h3 class="font-extrabold uppercase tracking-wider text-[13px] mb-4">LOYALTY</h3>
                    <ul class="space-y-3">
                        <li>
                            <a href="#" class="inline-flex items-center text-gray-700 hover:text-black transition">
                                <i class="fa-solid fa-shield-heart w-5 text-gray-800 text-sm"></i>
                                <span class="ml-2 font-medium">Membership & Benefits</span>
                            </a>
                        </li>
                    </ul>
                </div>

                <div>
                    <h3 class="font-extrabold uppercase tracking-wider text-[13px] mb-4">FOLLOW US</h3>
                    <ul class="space-y-3 font-medium text-gray-700">
                        <li><a href="#" class="inline-flex items-center hover:text-black transition"><i
                                    class="fa-brands fa-facebook w-5 text-gray-800 text-sm"></i><span
                                    class="ml-2">Facebook</span></a></li>
                        <li><a href="#" class="inline-flex items-center hover:text-black transition"><i
                                    class="fa-brands fa-instagram w-5 text-gray-800 text-sm"></i><span
                                    class="ml-2">Instagram</span></a></li>
                        <li><a href="#" class="inline-flex items-center hover:text-black transition"><i
                                    class="fa-brands fa-tiktok w-5 text-gray-800 text-sm"></i><span
                                    class="ml-2">TikTok</span></a></li>
                        <li><a href="#" class="inline-flex items-center hover:text-black transition"><i
                                    class="fa-brands fa-youtube w-5 text-gray-800 text-sm"></i><span
                                    class="ml-2">Youtube</span></a></li>
                    </ul>
                </div>

                <div>
                    <h3 class="font-extrabold uppercase tracking-wider text-[13px] mb-4">CUSTOMER SERVICES</h3>
                    <ul class="space-y-3 font-medium text-gray-700">
                        <li><a href="#" class="inline-flex items-center hover:text-black transition"><i
                                    class="fa-solid fa-circle-question w-5 text-gray-800 text-sm"></i><span
                                    class="ml-2">Online exchange policy</span></a></li>
                        <li><a href="#" class="inline-flex items-center hover:text-black transition"><i
                                    class="fa-solid fa-shield-halved w-5 text-gray-800 text-sm"></i><span
                                    class="ml-2">Privacy Policy</span></a></li>
                        <li><a href="#" class="inline-flex items-center hover:text-black transition"><i
                                    class="fa-solid fa-comments w-5 text-gray-800 text-sm"></i><span class="ml-2">FAQs &
                                    guides</span></a></li>
                        <li><a href="#" class="inline-flex items-center hover:text-black transition"><i
                                    class="fa-solid fa-location-dot w-5 text-gray-800 text-sm"></i><span
                                    class="ml-2">Find a store</span></a></li>
                    </ul>
                </div>

                <div>
                    <h3 class="font-extrabold uppercase tracking-wider text-[13px] mb-4">CONTACT US</h3>
                    <ul class="space-y-3 font-medium text-gray-700">
                        <li><a href="mailto:customer.care@zandokh.com"
                                class="inline-flex items-center hover:text-black transition"><i
                                    class="fa-solid fa-envelope w-5 text-gray-800 text-sm"></i><span
                                    class="ml-2 truncate">customer.care@lumorakh.com</span></a></li>
                        <li><a href="tel:+855085330330" class="inline-flex items-center hover:text-black transition"><i
                                    class="fa-solid fa-phone w-5 text-gray-800 text-sm"></i><span class="ml-2">(+855)
                                    093 886 305</span></a></li>
                        <li><a href="#" class="inline-flex items-center hover:text-black transition"><i
                                    class="fa-brands fa-telegram w-5 text-gray-800 text-sm"></i><span
                                    class="ml-2">Telegram</span></a></li>
                    </ul>
                </div>
            </div>

            <div class="mt-12">
                <h3 class="font-extrabold uppercase tracking-wider text-[13px] mb-4">WE ACCEPT</h3>
                <div class="space-y-2">
                    <div class="flex flex-wrap items-center gap-2">
                        <div
                            class="h-6 px-2 bg-[#004f71] text-white rounded text-[10px] font-bold flex items-center justify-center">
                            ABA PAY</div>
                        <div
                            class="h-6 px-2.5 bg-[#1a1f71] text-white rounded text-[10px] font-black italic flex items-center justify-center">
                            VISA</div>
                        <div class="h-6 px-2 bg-black rounded flex items-center justify-center gap-0.5">
                            <span class="h-3.5 w-3.5 bg-red-600 rounded-full inline-block"></span>
                            <span class="h-3.5 w-3.5 bg-amber-500 rounded-full inline-block -ml-2 opacity-90"></span>
                        </div>
                        <div
                            class="h-6 px-2 bg-[#006064] text-white rounded text-[9px] font-bold flex items-center justify-center">
                            UnionPay</div>
                        <div
                            class="h-6 px-2 bg-[#0d47a1] text-white rounded text-[10px] font-black flex items-center justify-center">
                            JCB</div>
                        <div
                            class="h-6 px-2 bg-[#1b5e20] text-white rounded text-[10px] font-bold flex items-center justify-center">
                            KHQR</div>
                    </div>
                </div>
            </div>
            <div class="mt-12 border-t border-gray-200"></div>
        </footer>

        <!-- ================= POPUP MODAL (LOGIN & REGISTER) ================= -->
        <div v-if="isModalOpen" class="fixed inset-0 bg-black/60 z-50 flex items-center justify-center p-4"
            @click.self="closeModal">
            <div class="bg-white w-full max-w-md rounded-xl shadow-2xl overflow-hidden relative">
                <button @click="closeModal"
                    class="absolute top-5 right-5 text-gray-400 hover:text-black text-xl transition">
                    <i class="fa-solid fa-xmark"></i>
                </button>

                <div class="border-b border-gray-200 px-6 pt-5 flex space-x-6 text-sm font-bold tracking-wider">
                    <button @click="currentTab = 'login'"
                        :class="currentTab === 'login' ? 'pb-3 border-b-2 border-black text-black' : 'pb-3 border-b-2 border-transparent text-gray-400 hover:text-black'">
                        LOGIN
                    </button>
                    <button @click="currentTab = 'register'"
                        :class="currentTab === 'register' ? 'pb-3 border-b-2 border-black text-black' : 'pb-3 border-b-2 border-transparent text-gray-400 hover:text-black'">
                        REGISTER
                    </button>
                </div>

                <div class="p-6 max-h-[85vh] overflow-y-auto">
                    <!-- REGISTER FORM -->
                    <form v-if="currentTab === 'register'" class="space-y-4" @submit.prevent>
                        <div class="flex items-center space-x-4 text-xs font-medium text-gray-700">
                            <span>Gender (Required)</span>
                            <label class="inline-flex items-center cursor-pointer">
                                <input type="radio" name="gender" value="male"
                                    class="text-black focus:ring-black accent-black" />
                                <span class="ml-1.5 text-xs text-gray-800">Male</span>
                            </label>
                            <label class="inline-flex items-center cursor-pointer">
                                <input type="radio" name="gender" value="female"
                                    class="text-black focus:ring-black accent-black" />
                                <span class="ml-1.5 text-xs text-gray-800">Female</span>
                            </label>
                        </div>
                        <div class="grid grid-cols-2 gap-3">
                            <div>
                                <label class="block text-xs text-gray-600 mb-1">First name</label>
                                <input type="text" placeholder="Enter first name"
                                    class="w-full border border-gray-300 rounded px-3 py-2 text-xs focus:outline-none focus:border-black transition" />
                            </div>
                            <div>
                                <label class="block text-xs text-gray-600 mb-1">Last name</label>
                                <input type="text" placeholder="Enter last name"
                                    class="w-full border border-gray-300 rounded px-3 py-2 text-xs focus:outline-none focus:border-black transition" />
                            </div>
                        </div>
                        <div>
                            <label class="block text-xs text-gray-600 mb-1">Mobile number</label>
                            <input type="tel" placeholder="Enter phone number"
                                class="w-full border border-gray-300 rounded px-3 py-2 text-xs focus:outline-none focus:border-black transition" />
                        </div>
                        <div>
                            <label class="block text-xs text-gray-600 mb-1">Email</label>
                            <input type="email" placeholder="Enter email"
                                class="w-full border border-gray-300 rounded px-3 py-2 text-xs focus:outline-none focus:border-black transition" />
                        </div>
                        <button type="submit"
                            class="w-full bg-black hover:bg-neutral-900 text-white font-bold py-3 rounded text-xs tracking-wider uppercase transition">CREATE
                            ACCOUNT</button>
                    </form>

                    <!-- LOGIN FORM -->
                    <form v-if="currentTab === 'login'" class="space-y-4" @submit.prevent>
                        <div>
                            <label class="block text-xs text-gray-600 mb-1">Email or Mobile number</label>
                            <input type="text" placeholder="Enter email or phone number"
                                class="w-full border border-gray-300 rounded px-3 py-2 text-xs focus:outline-none focus:border-black transition" />
                        </div>
                        <div>
                            <label class="text-xs text-gray-600 block mb-1">Password</label>
                            <input type="password" placeholder="Enter your password"
                                class="w-full border border-gray-300 rounded px-3 py-2 text-xs focus:outline-none focus:border-black transition" />
                        </div>
                        <button type="submit"
                            class="w-full bg-black hover:bg-neutral-900 text-white font-bold py-3 rounded text-xs tracking-wider uppercase transition">LOGIN</button>
                    </form>
                </div>
            </div>
        </div>

    </div>
</template>

<script setup>
import { ref } from 'vue'

const isModalOpen = ref(false)
const currentTab = ref('login')

const openModal = (tab = 'login') => {
    currentTab.value = tab
    isModalOpen.value = true
}

const closeModal = () => {
    isModalOpen.value = false
}
</script>

<style scoped>
nav a {
    font-family: 'Montserrat', sans-serif;
    font-weight: 900;
    letter-spacing: -0.02em;
}
</style>