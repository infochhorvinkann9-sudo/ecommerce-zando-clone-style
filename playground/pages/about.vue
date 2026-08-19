<!-- pages/about.vue -->
<template>
    <main class="max-w-7xl mx-auto px-4 sm:px-6 py-12 space-y-16 font-['Montserrat',sans-serif]">

        <!-- ================= HERO SECTION ================= -->
        <section class="text-center max-w-3xl mx-auto space-y-4">
            <span class="text-xs font-black tracking-widest text-red-600 uppercase bg-red-50 px-3 py-1 rounded-full">
                About Our Brand
            </span>
            <h1 class="text-3xl sm:text-5xl font-black uppercase tracking-tight text-gray-900 leading-tight">
                Redefining Everyday Fashion
            </h1>
            <p class="text-gray-600 text-xs sm:text-sm leading-relaxed">
                Lumora is Cambodia's premier fashion and lifestyle destination, dedicated to delivering trendsetting
                designs, effortless elegance, and exceptional quality for modern living.
            </p>
        </section>

        <!-- ================= STORY & SHOWCASE ================= -->
        <section class="grid grid-cols-1 lg:grid-cols-2 gap-10 items-center">
            <div class="relative rounded-2xl overflow-hidden shadow-md aspect-[4/3] bg-gray-100 group">
                <img src="https://images.unsplash.com/photo-1441986300917-64674bd600d8?auto=format&fit=crop&w=900&q=80"
                    alt="Lumora Storefront"
                    class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500" />
                <div class="absolute inset-0 bg-gradient-to-t from-black/50 via-transparent to-transparent"></div>
                <div class="absolute bottom-6 left-6 text-white">
                    <p class="text-xs font-bold uppercase tracking-widest text-red-400">Flagship Experience</p>
                    <h3 class="text-lg font-black uppercase">Phnom Penh & Across Cambodia</h3>
                </div>
            </div>

            <div class="space-y-6">
                <div class="space-y-2">
                    <h2 class="text-2xl font-black uppercase tracking-tight text-gray-900">
                        Our Journey & Passion
                    </h2>
                    <div class="w-12 h-1 bg-red-600 rounded"></div>
                </div>
                <p class="text-gray-600 text-xs sm:text-sm leading-relaxed">
                    Founded with a simple mission: to make premium everyday apparel accessible, stylish, and
                    comfortable. From casual basics to high-street statement pieces, every collection is curated to
                    inspire confidence.
                </p>
                <p class="text-gray-600 text-xs sm:text-sm leading-relaxed">
                    We combine seamless e-commerce ordering with dynamic retail locations, ensuring fast nationwide
                    delivery, effortless exchanges, and friendly customer care.
                </p>

                <!-- Stats -->
                <div class="grid grid-cols-3 gap-4 pt-4 border-t border-gray-100">
                    <div class="p-3 bg-gray-50 rounded-xl text-center">
                        <h4 class="text-xl sm:text-2xl font-black text-black">100%</h4>
                        <p class="text-[10px] text-gray-500 font-bold uppercase mt-0.5">Authentic</p>
                    </div>
                    <div class="p-3 bg-gray-50 rounded-xl text-center">
                        <h4 class="text-xl sm:text-2xl font-black text-black">25+</h4>
                        <p class="text-[10px] text-gray-500 font-bold uppercase mt-0.5">Locations</p>
                    </div>
                    <div class="p-3 bg-gray-50 rounded-xl text-center">
                        <h4 class="text-xl sm:text-2xl font-black text-black">24/7</h4>
                        <p class="text-[10px] text-gray-500 font-bold uppercase mt-0.5">Support</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- ================= CORE VALUES ================= -->
        <section class="space-y-8 pt-4">
            <div class="text-center space-y-2">
                <h2 class="text-2xl font-black uppercase tracking-tight text-gray-900">Why Choose Us</h2>
                <p class="text-xs text-gray-500">Committed to quality, style, and satisfaction.</p>
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
                <div class="p-6 border border-gray-200 rounded-xl bg-white shadow-sm space-y-3">
                    <div class="w-10 h-10 bg-black text-white rounded-lg flex items-center justify-center">
                        <i class="fa-solid fa-shirt text-sm"></i>
                    </div>
                    <h3 class="font-black text-xs uppercase tracking-wider text-gray-900">Curated Quality</h3>
                    <p class="text-xs text-gray-500 leading-relaxed">
                        Durable fabrics and tailored silhouettes designed for lasting comfort.
                    </p>
                </div>

                <div class="p-6 border border-gray-200 rounded-xl bg-white shadow-sm space-y-3">
                    <div class="w-10 h-10 bg-black text-white rounded-lg flex items-center justify-center">
                        <i class="fa-solid fa-truck-fast text-sm"></i>
                    </div>
                    <h3 class="font-black text-xs uppercase tracking-wider text-gray-900">Fast Nationwide Delivery</h3>
                    <p class="text-xs text-gray-500 leading-relaxed">
                        Quick fulfillment to all provinces and major cities in Cambodia.
                    </p>
                </div>

                <div class="p-6 border border-gray-200 rounded-xl bg-white shadow-sm space-y-3">
                    <div class="w-10 h-10 bg-black text-white rounded-lg flex items-center justify-center">
                        <i class="fa-solid fa-rotate-left text-sm"></i>
                    </div>
                    <h3 class="font-black text-xs uppercase tracking-wider text-gray-900">Easy Exchange</h3>
                    <p class="text-xs text-gray-500 leading-relaxed">
                        Hassle-free sizing exchanges online and at any of our retail stores.
                    </p>
                </div>

                <div class="p-6 border border-gray-200 rounded-xl bg-white shadow-sm space-y-3">
                    <div class="w-10 h-10 bg-black text-white rounded-lg flex items-center justify-center">
                        <i class="fa-solid fa-shield-halved text-sm"></i>
                    </div>
                    <h3 class="font-black text-xs uppercase tracking-wider text-gray-900">Secure Payments</h3>
                    <p class="text-xs text-gray-500 leading-relaxed">
                        Support for KHQR, ABA PAY, Wing, Credit Cards, and Cash on Delivery.
                    </p>
                </div>
            </div>
        </section>

    </main>
</template>

<script setup>
useHead({
    title: 'About Us - LUMORA Store'
})
</script>