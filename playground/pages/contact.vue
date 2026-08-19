<template>
    <main class="max-w-7xl mx-auto px-4 sm:px-6 py-10 space-y-12">
        <!-- Header Title -->
        <div class="text-center max-w-2xl mx-auto space-y-2">
            <p class="text-xs font-bold tracking-widest text-red-500 uppercase">
                Customer Support
            </p>
            <h1 class="text-3xl sm:text-4xl font-black uppercase tracking-tight">
                Get in Touch With Us
            </h1>
            <p class="text-gray-500 text-xs sm:text-sm">
                Have a question about orders, delivery, or sizing? Our team in Cambodia is here to assist you.
            </p>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
            <!-- Contact Cards -->
            <div class="space-y-4">
                <!-- Call -->
                <div class="p-5 border border-gray-200 rounded-xl bg-gray-50 flex items-start space-x-4">
                    <div
                        class="w-10 h-10 bg-black text-white rounded-lg flex items-center justify-center flex-shrink-0">
                        <i class="fa-solid fa-phone"></i>
                    </div>
                    <div>
                        <h3 class="font-bold text-xs uppercase text-gray-900">Phone Support</h3>
                        <p class="text-xs text-gray-500 mt-0.5">Mon - Sun, 8:00 AM - 9:00 PM</p>
                        <a href="tel:+855085330330" class="text-xs font-bold text-black hover:underline mt-1 block">
                            (+855) 093 886 306
                        </a>
                    </div>
                </div>

                <!-- Email -->
                <div class="p-5 border border-gray-200 rounded-xl bg-gray-50 flex items-start space-x-4">
                    <div
                        class="w-10 h-10 bg-black text-white rounded-lg flex items-center justify-center flex-shrink-0">
                        <i class="fa-solid fa-envelope"></i>
                    </div>
                    <div>
                        <h3 class="font-bold text-xs uppercase text-gray-900">Email Inquiries</h3>
                        <p class="text-xs text-gray-500 mt-0.5">We usually reply within 24 hours.</p>
                        <a href="mailto:customer.care@zandokh.com"
                            class="text-xs font-bold text-black hover:underline mt-1 block">
                            customer.care@lumorakh.com
                        </a>
                    </div>
                </div>

                <!-- Telegram -->
                <div class="p-5 border border-gray-200 rounded-xl bg-gray-50 flex items-start space-x-4">
                    <div
                        class="w-10 h-10 bg-[#229ED9] text-white rounded-lg flex items-center justify-center flex-shrink-0">
                        <i class="fa-brands fa-telegram text-lg"></i>
                    </div>
                    <div>
                        <h3 class="font-bold text-xs uppercase text-gray-900">Telegram Channel</h3>
                        <p class="text-xs text-gray-500 mt-0.5">Instant chat & order tracking.</p>
                        <a href="#" class="text-xs font-bold text-black hover:underline mt-1 block">
                            @Lumoracambodia
                        </a>
                    </div>
                </div>
            </div>

            <!-- Contact Form -->
            <div class="lg:col-span-2 bg-white border border-gray-200 rounded-xl p-6 sm:p-8 shadow-sm">
                <h2 class="text-lg font-extrabold uppercase tracking-tight mb-4">
                    Send Us a Direct Message
                </h2>

                <form class="space-y-4" @submit.prevent="handleSubmit">
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                        <div>
                            <label class="block text-xs font-semibold text-gray-700 mb-1">
                                Your Full Name <span class="text-red-500">*</span>
                            </label>
                            <input v-model="form.name" type="text" placeholder="John Doe"
                                class="w-full border border-gray-300 rounded px-3 py-2 text-xs focus:outline-none focus:border-black transition"
                                required />
                        </div>
                        <div>
                            <label class="block text-xs font-semibold text-gray-700 mb-1">
                                Email Address <span class="text-red-500">*</span>
                            </label>
                            <input v-model="form.email" type="email" placeholder="john@example.com"
                                class="w-full border border-gray-300 rounded px-3 py-2 text-xs focus:outline-none focus:border-black transition"
                                required />
                        </div>
                    </div>

                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                        <div>
                            <label class="block text-xs font-semibold text-gray-700 mb-1">Phone Number</label>
                            <input v-model="form.phone" type="tel" placeholder="(+855) 12 345 678"
                                class="w-full border border-gray-300 rounded px-3 py-2 text-xs focus:outline-none focus:border-black transition" />
                        </div>
                        <div>
                            <label class="block text-xs font-semibold text-gray-700 mb-1">Subject</label>
                            <select v-model="form.subject"
                                class="w-full border border-gray-300 rounded px-3 py-2 text-xs text-gray-700 bg-white focus:outline-none focus:border-black transition cursor-pointer">
                                <option>Order & Tracking Inquiry</option>
                                <option>Exchange & Returns</option>
                                <option>Product Inquiries</option>
                                <option>General Feedback</option>
                            </select>
                        </div>
                    </div>

                    <div>
                        <label class="block text-xs font-semibold text-gray-700 mb-1">
                            Your Message <span class="text-red-500">*</span>
                        </label>
                        <textarea v-model="form.message" rows="5" placeholder="Write your message here..."
                            class="w-full border border-gray-300 rounded px-3 py-2 text-xs focus:outline-none focus:border-black transition"
                            required></textarea>
                    </div>

                    <button type="submit"
                        class="bg-black hover:bg-neutral-900 text-white font-bold py-3 px-8 rounded text-xs tracking-wider uppercase transition">
                        SUBMIT MESSAGE
                    </button>
                </form>
            </div>
        </div>
    </main>
</template>

<script setup>
import { reactive } from 'vue'

useHead({
    title: 'Contact Us - LUMORA'
})

const form = reactive({
    name: '',
    email: '',
    phone: '',
    subject: 'Order & Tracking Inquiry',
    message: ''
})

const handleSubmit = () => {
    alert(`Thank ${form.name}!`)
    form.name = ''
    form.email = ''
    form.phone = ''
    form.message = ''
}
</script>