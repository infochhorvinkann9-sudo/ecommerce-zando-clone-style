<!-- pages/index.vue -->
<template>
    <main class="max-w-7xl mx-auto px-4 sm:px-6 py-4 space-y-10">

        <!-- ================= HERO BANNER ================= -->
        <section
            class="relative w-full rounded-lg overflow-hidden hero-gradient text-white text-center py-20 px-4 md:py-28 shadow-sm">
            <div class="relative z-10 max-w-2xl mx-auto space-y-4">
                <h1
                    class="text-3xl sm:text-5xl md:text-6xl font-black uppercase tracking-tight leading-none drop-shadow-md">
                    Exclusive Discount
                </h1>
                <p class="text-base sm:text-xl font-bold tracking-widest uppercase text-white/90">
                    On New Arrivals
                </p>
                <p class="text-[10px] text-white/60 tracking-wider">T&Cs Apply</p>

                <div class="flex justify-center gap-4 pt-4">
                    <NuxtLink to="/category/men's clothing"
                        class="border border-white/70 bg-black/40 hover:bg-black text-white text-xs font-bold py-2.5 px-8 uppercase tracking-wider rounded transition">
                        Men
                    </NuxtLink>
                    <NuxtLink to="/category/women's clothing"
                        class="border border-white/70 bg-black/40 hover:bg-black text-white text-xs font-bold py-2.5 px-8 uppercase tracking-wider rounded transition">
                        Women
                    </NuxtLink>
                </div>
            </div>
        </section>

        <!-- ================= BRAND LOGO TILES ================= -->
        <section class="grid grid-cols-3 sm:grid-cols-6 gap-2 sm:gap-3">
            <div
                class="bg-black text-white py-3 px-2 rounded flex items-center justify-center font-black tracking-tight text-sm uppercase">
                ZANDO.
            </div>
            <div
                class="bg-black text-white py-3 px-2 rounded flex items-center justify-center font-bold tracking-tighter text-xs uppercase">
                TEN & ELEVEN
            </div>
            <div
                class="bg-black text-white py-3 px-2 rounded flex items-center justify-center font-mono font-bold tracking-widest text-xs uppercase">
                ROUTINE
            </div>
            <div
                class="bg-black text-white py-3 px-2 rounded flex items-center justify-center font-bold tracking-wider text-[11px] uppercase">
                TAG SPACE
            </div>
            <div
                class="bg-black text-white py-3 px-2 rounded flex items-center justify-center font-black text-sm italic uppercase">
                361°
            </div>
            <div
                class="bg-black text-white py-3 px-2 rounded flex items-center justify-center font-bold tracking-tight text-xs uppercase">
                Pomelo.
            </div>
        </section>

        <!-- ================= SECONDARY CAMPAIGN BANNER ================= -->
        <section
            class="relative w-full rounded-lg overflow-hidden bg-rose-100 border border-pink-200 py-10 px-6 sm:px-12 flex flex-col md:flex-row items-center justify-between gap-6">
            <div class="text-center md:text-left">
                <span class="font-serif italic text-3xl sm:text-4xl text-red-400 block leading-tight">
                    Obsessed Over The Dots
                </span>
            </div>
            <div class="flex items-center space-x-6">
                <img src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&w=400&q=80"
                    alt="Model preview" class="h-28 w-28 object-cover rounded-full border-2 border-white shadow-md" />
                <span class="text-lg font-black tracking-widest text-gray-800 uppercase">
                    TEN & ELEVEN
                </span>
            </div>
        </section>

        <!-- ================= LOADING STATE ================= -->
        <div v-if="pending" class="grid grid-cols-2 sm:grid-cols-4 gap-4 py-8">
            <div v-for="i in 8" :key="i" class="animate-pulse space-y-3">
                <div class="bg-gray-200 aspect-square rounded-md"></div>
                <div class="h-4 bg-gray-200 rounded w-1/2"></div>
                <div class="h-3 bg-gray-200 rounded w-3/4"></div>
            </div>
        </div>

        <!-- ================= ERROR STATE ================= -->
        <div v-else-if="error" class="text-center py-12 text-red-600 font-bold text-sm">
            (Failed to load products)
        </div>

        <!-- ================= PRODUCT SECTIONS ================= -->
        <div v-else class="space-y-12">

            <!-- Section 1: Women's Clothing -->
            <div class="grid grid-cols-2 sm:grid-cols-4 gap-4 relative">
                <NuxtLink v-for="product in womenProducts" :key="product.id" :to="`/products/${product.id}`"
                    class="group relative flex flex-col cursor-pointer">
                    <div
                        class="relative bg-gray-50 aspect-square rounded overflow-hidden p-4 flex items-center justify-center border border-gray-100">
                        <span
                            class="absolute top-2 left-2 bg-red-600 text-white text-[10px] font-bold px-1.5 py-0.5 rounded z-10">
                            -20%
                        </span>
                        <img :src="product.image" :alt="product.title"
                            class="max-h-full max-w-full object-contain group-hover:scale-105 transition duration-300" />
                    </div>

                    <div class="mt-2 text-xs">
                        <div class="flex items-center justify-between">
                            <div>
                                <span class="font-bold text-red-600">US ${{ Number(product.price).toFixed(2) }}</span>
                                <span class="text-gray-400 line-through text-[11px] ml-1">
                                    US ${{ (product.price * 1.25).toFixed(2) }}
                                </span>
                            </div>

                            <button class="text-gray-400 hover:text-red-500 transition" @click.prevent>
                                <i class="fa-regular fa-heart"></i>
                            </button>
                        </div>

                        <p class="text-gray-700 font-medium truncate mt-1 group-hover:text-black"
                            :title="product.title">
                            {{ product.title }}
                        </p>
                    </div>
                </NuxtLink>
            </div>

            <!-- Section 2: Men's Clothing & Recommendations -->
            <div class="grid grid-cols-2 sm:grid-cols-4 gap-4 relative">
                <NuxtLink v-for="product in menProducts" :key="product.id" :to="`/products/${product.id}`"
                    class="group relative flex flex-col cursor-pointer">
                    <div
                        class="relative bg-gray-50 aspect-square rounded overflow-hidden p-4 flex items-center justify-center border border-gray-100">
                        <span
                            class="absolute top-2 left-2 bg-red-600 text-white text-[10px] font-bold px-1.5 py-0.5 rounded z-10">
                            -15%
                        </span>
                        <img :src="product.image" :alt="product.title"
                            class="max-h-full max-w-full object-contain group-hover:scale-105 transition duration-300" />
                    </div>

                    <div class="mt-2 text-xs">
                        <div class="flex items-center justify-between">
                            <div>
                                <span class="font-bold text-red-600">US ${{ Number(product.price).toFixed(2) }}</span>
                                <span class="text-gray-400 line-through text-[11px] ml-1">
                                    US ${{ (product.price * 1.15).toFixed(2) }}
                                </span>
                            </div>

                            <button class="text-gray-400 hover:text-red-500 transition" @click.prevent>
                                <i class="fa-regular fa-heart"></i>
                            </button>
                        </div>

                        <p class="text-gray-700 font-medium uppercase truncate mt-1 group-hover:text-black"
                            :title="product.title">
                            {{ product.title }}
                        </p>

                        <div class="flex space-x-1 mt-1">
                            <span class="h-2 w-2 rounded-full bg-black inline-block"></span>
                            <span class="h-2 w-2 rounded-full bg-gray-400 inline-block"></span>
                        </div>
                    </div>
                </NuxtLink>
            </div>

        </div>
    </main>
</template>

<script setup>
useHead({
    title: 'ZANDO - Fashion & Lifestyle Store'
})

// Fetch Products from FakeStoreAPI
const { data: products, pending, error } = await useFetch('https://fakestoreapi.com/products')

const womenProducts = computed(() => {
    if (!products.value) return []
    return products.value.filter(p => p.category === "women's clothing").slice(0, 4)
})

const menProducts = computed(() => {
    if (!products.value) return []
    return products.value.filter(p => p.category === "men's clothing").slice(0, 4)
})
</script>

<style scoped>
.hero-gradient {
    background: radial-gradient(circle at center,
            #ff5e18 0%,
            #b82b00 45%,
            #420800 100%);
}
</style>