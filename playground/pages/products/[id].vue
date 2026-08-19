<!-- pages/products/[id].vue -->
<template>
    <div class="max-w-7xl mx-auto px-4 sm:px-6 py-6 font-['Montserrat',sans-serif]">

        <!-- ================= LOADING STATE ================= -->
        <div v-if="pending" class="space-y-8 animate-pulse py-8">
            <div class="h-4 bg-gray-200 rounded w-1/4"></div>
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-10">
                <div class="lg:col-span-7 bg-gray-200 aspect-[3/4] rounded-xl"></div>
                <div class="lg:col-span-5 space-y-4">
                    <div class="h-6 bg-gray-200 rounded w-3/4"></div>
                    <div class="h-8 bg-gray-200 rounded w-1/3"></div>
                    <div class="h-24 bg-gray-200 rounded w-full"></div>
                </div>
            </div>
        </div>

        <!-- ================= ERROR / NOT FOUND ================= -->
        <div v-else-if="error || !product" class="text-center py-20 space-y-4">
            <h2 class="text-2xl font-black uppercase text-gray-800">រកមិនឃើញផលិតផលនេះទេ (Product Not Found)</h2>
            <NuxtLink to="/" class="inline-block bg-black text-white px-6 py-2.5 rounded text-xs font-bold uppercase">
                ត្រឡប់ទៅទំព័រដើម
            </NuxtLink>
        </div>

        <!-- ================= MAIN PRODUCT DETAIL ================= -->
        <div v-else class="space-y-16">
            <!-- Breadcrumb -->
            <nav aria-label="Breadcrumb">
                <ol class="flex items-center space-x-2 text-xs text-gray-500 uppercase tracking-wider font-semibold">
                    <li>
                        <NuxtLink to="/" class="hover:text-black">Home</NuxtLink>
                    </li>
                    <li><span class="text-gray-300">/</span></li>
                    <li><span class="hover:text-black cursor-pointer">{{ product.category }}</span></li>
                    <li><span class="text-gray-300">/</span></li>
                    <li class="text-black font-extrabold truncate max-w-[200px] sm:max-w-xs">{{ product.title }}</li>
                </ol>
            </nav>

            <main class="space-y-16">
                <div class="grid grid-cols-1 lg:grid-cols-12 gap-10">

                    <!-- Left Column: Gallery (7 Cols) -->
                    <div class="lg:col-span-7 flex flex-col-reverse md:flex-row gap-4">
                        <!-- Thumbnails -->
                        <div class="flex md:flex-col gap-3 overflow-x-auto md:overflow-visible">
                            <button v-for="(img, index) in thumbnails" :key="index" @click="selectedImage = img" :class="[
                                'w-16 h-20 md:w-20 md:h-24 rounded overflow-hidden flex-shrink-0 focus:outline-none transition p-1 bg-white',
                                selectedImage === img ? 'border-2 border-black' : 'border border-gray-200'
                            ]">
                                <img :src="img" :alt="`${product.title} - ${index + 1}`"
                                    class="w-full h-full object-contain" />
                            </button>
                        </div>

                        <!-- Main Display Image -->
                        <div
                            class="relative flex-1 bg-gray-50 rounded-xl overflow-hidden aspect-[3/4] p-8 flex items-center justify-center border border-gray-100">
                            <span
                                class="absolute top-4 left-4 bg-red-600 text-white text-xs font-black px-2 py-1 rounded z-10">
                                -15%
                            </span>
                            <img :src="selectedImage" :alt="product.title"
                                class="max-h-full max-w-full object-contain transition-transform duration-300 hover:scale-105" />
                        </div>
                    </div>

                    <!-- Right Column: Product Actions & Info (5 Cols) -->
                    <div class="lg:col-span-5 space-y-6">

                        <!-- Title & Brand -->
                        <div class="border-b border-gray-100 pb-4">
                            <p class="text-xs font-black uppercase tracking-widest text-gray-500">
                                {{ product.category }}
                            </p>
                            <h1
                                class="text-xl sm:text-2xl font-black uppercase tracking-tight text-gray-900 mt-1 leading-snug">
                                {{ product.title }}
                            </h1>
                            <div class="flex items-center space-x-2 mt-1">
                                <span class="text-xs text-gray-400 font-bold">SKU: ZAN-{{ product.id }}-2026</span>
                                <span class="text-xs text-gray-300">•</span>
                                <div class="flex items-center text-amber-400 text-xs">
                                    <i class="fa-solid fa-star"></i>
                                    <span class="text-gray-600 font-bold ml-1">{{ product.rating?.rate || '4.5' }} ({{
                                        product.rating?.count || 0 }})</span>
                                </div>
                            </div>

                            <!-- Price -->
                            <div class="flex items-center space-x-3 mt-4">
                                <span class="text-2xl font-black text-red-600">
                                    US ${{ Number(product.price).toFixed(2) }}
                                </span>
                                <span class="text-sm font-semibold text-gray-400 line-through">
                                    US ${{ (product.price * 1.15).toFixed(2) }}
                                </span>
                                <span class="text-xs bg-red-50 text-red-600 font-extrabold px-2 py-0.5 rounded">
                                    Save 15%
                                </span>
                            </div>
                        </div>

                        <!-- Color Selection -->
                        <div>
                            <label class="block text-xs font-extrabold uppercase tracking-wide mb-2">
                                Color: <span class="text-gray-500 font-medium">{{ selectedColor }}</span>
                            </label>
                            <div class="flex items-center space-x-3">
                                <button v-for="color in colors" :key="color.name" @click="selectedColor = color.name"
                                    :class="[
                                        'w-8 h-8 rounded-full border-2 focus:outline-none transition',
                                        color.bg,
                                        selectedColor === color.name ? 'border-black scale-110' : 'border-transparent'
                                    ]"></button>
                            </div>
                        </div>

                        <!-- Size Selection -->
                        <div>
                            <div class="flex items-center justify-between mb-2">
                                <label class="text-xs font-extrabold uppercase tracking-wide">Select Size</label>
                                <button class="text-xs text-gray-500 hover:text-black underline font-bold">
                                    Size Guide
                                </button>
                            </div>
                            <div class="grid grid-cols-4 gap-2">
                                <button v-for="size in sizes" :key="size" @click="selectedSize = size" :class="[
                                    'py-2.5 text-xs font-extrabold rounded uppercase transition',
                                    selectedSize === size
                                        ? 'border-2 border-black bg-black text-white'
                                        : 'border border-gray-300 hover:border-black text-gray-800'
                                ]">
                                    {{ size }}
                                </button>
                            </div>
                        </div>

                        <!-- Quantity & Add to Bag -->
                        <div class="space-y-3 pt-2">
                            <div class="flex items-center gap-3">
                                <!-- Counter -->
                                <div class="flex items-center border border-gray-300 rounded bg-white">
                                    <button @click="updateQty(-1)"
                                        class="w-10 h-11 flex items-center justify-center text-gray-500 hover:text-black">
                                        <i class="fa-solid fa-minus text-xs"></i>
                                    </button>
                                    <input type="text" :value="quantity" readonly
                                        class="w-10 text-center text-xs font-black focus:outline-none bg-transparent" />
                                    <button @click="updateQty(1)"
                                        class="w-10 h-11 flex items-center justify-center text-gray-500 hover:text-black">
                                        <i class="fa-solid fa-plus text-xs"></i>
                                    </button>
                                </div>

                                <!-- Add to Cart -->
                                <button @click="addToCart"
                                    class="flex-1 bg-black hover:bg-neutral-900 text-white font-black h-11 rounded text-xs uppercase tracking-wider flex items-center justify-center space-x-2 transition shadow-sm">
                                    <i class="fa-solid fa-bag-shopping text-sm"></i>
                                    <span>ADD TO SHOPPING BAG</span>
                                </button>

                                <!-- Wishlist -->
                                <button
                                    class="w-11 h-11 border border-gray-300 hover:border-black rounded flex items-center justify-center text-gray-700 hover:text-red-500 transition">
                                    <i class="fa-regular fa-heart text-base"></i>
                                </button>
                            </div>
                        </div>

                        <!-- Highlights -->
                        <div class="p-4 bg-gray-50 rounded-xl border border-gray-200 space-y-3 text-xs">
                            <div class="flex items-center space-x-3 text-gray-700">
                                <i class="fa-solid fa-truck-fast text-base text-gray-900 w-5"></i>
                                <div>
                                    <p class="font-black text-gray-900">Fast Nationwide Shipping</p>
                                    <p class="text-gray-500 text-[11px]">1-2 business days in Phnom Penh; 2-3 days for
                                        provinces.</p>
                                </div>
                            </div>
                            <div class="flex items-center space-x-3 text-gray-700">
                                <i class="fa-solid fa-rotate-left text-base text-gray-900 w-5"></i>
                                <div>
                                    <p class="font-black text-gray-900">7-Day Free Exchange Policy</p>
                                    <p class="text-gray-500 text-[11px]">Hassle-free size exchanges at any retail
                                        branch.</p>
                                </div>
                            </div>
                        </div>

                        <!-- Description -->
                        <div class="border-t border-gray-200 pt-4 space-y-2 text-xs leading-relaxed text-gray-600">
                            <h3 class="font-black text-gray-900 uppercase">Product Description</h3>
                            <p>{{ product.description }}</p>
                        </div>

                    </div>
                </div>

                <!-- ================= RELATED PRODUCTS ================= -->
                <section v-if="relatedProducts.length" class="space-y-4 pt-10 border-t border-gray-200">
                    <div class="flex items-center justify-between">
                        <h2 class="text-base sm:text-lg font-black uppercase tracking-tight">
                            You May Also Like
                        </h2>
                        <NuxtLink to="/" class="text-xs font-black text-gray-500 hover:text-black uppercase">
                            SEE ALL
                        </NuxtLink>
                    </div>

                    <div class="grid grid-cols-2 sm:grid-cols-4 gap-4">
                        <div v-for="item in relatedProducts" :key="item.id" class="group flex flex-col cursor-pointer"
                            @click="navigateTo(`/products/${item.id}`)">
                            <div
                                class="bg-gray-50 aspect-square rounded-xl overflow-hidden relative p-4 border border-gray-100 flex items-center justify-center">
                                <span
                                    class="absolute top-2 left-2 bg-red-600 text-white text-[10px] font-black px-1.5 py-0.5 rounded z-10">
                                    -15%
                                </span>
                                <img :src="item.image" :alt="item.title"
                                    class="max-h-full max-w-full object-contain group-hover:scale-105 transition duration-300" />
                            </div>
                            <div class="mt-2 text-xs space-y-1">
                                <div class="flex items-center justify-between">
                                    <span class="font-black text-red-600">US ${{ Number(item.price).toFixed(2) }}</span>
                                    <button class="text-gray-400 hover:text-red-500" @click.stop>
                                        <i class="fa-regular fa-heart"></i>
                                    </button>
                                </div>
                                <p class="text-gray-800 font-bold truncate">{{ item.title }}</p>
                            </div>
                        </div>
                    </div>
                </section>
            </main>
        </div>

    </div>
</template>

<script setup>
import { ref, computed, watchEffect } from 'vue'

const route = useRoute()
const productId = route.params.id

// Fetch Single Product
const { data: product, pending, error } = await useFetch(`https://fakestoreapi.com/products/${productId}`)

// Fetch Related Products (same category)
const { data: allProducts } = await useFetch('https://fakestoreapi.com/products')

const relatedProducts = computed(() => {
    if (!allProducts.value || !product.value) return []
    return allProducts.value
        .filter(p => p.category === product.value.category && p.id !== product.value.id)
        .slice(0, 4)
})

// Gallery & State
const selectedImage = ref('')
const selectedColor = ref('Off-White')
const selectedSize = ref('S')
const quantity = ref(1)

const colors = [
    { name: 'Off-White', bg: 'bg-stone-100' },
    { name: 'Charcoal Black', bg: 'bg-neutral-900' },
    { name: 'Soft Rose', bg: 'bg-pink-200' }
]

const sizes = ['XS', 'S', 'M', 'L']

const thumbnails = computed(() => {
    if (!product.value?.image) return []
    return [product.value.image, product.value.image, product.value.image]
})

watchEffect(() => {
    if (product.value?.image) {
        selectedImage.value = product.value.image
    }
})

const updateQty = (val) => {
    const newQty = quantity.value + val
    if (newQty >= 1 && newQty <= 10) {
        quantity.value = newQty
    }
}

const addToCart = () => {
    alert(`បានបន្ថែម ${product.value.title} (${selectedSize.value}, ${selectedColor.value}) ចំនួន ${quantity.value} ទៅក្នុងកន្ត្រក!`)
}

// ================= SEO META CONFIGURATION =================
useSeoMeta({
    title: () => product.value ? `${product.value.title} - LUMORA` : 'Product Detail - LUMORA',
    ogTitle: () => product.value ? `${product.value.title} - LUMORA Store` : 'LUMORA Fashion',
    description: () => product.value?.description || 'Discover trendy clothing and accessories at LUMORA Cambodia.',
    ogDescription: () => product.value?.description || 'Exclusive discounts on top trends at LUMORA.',
    ogImage: () => product.value?.image || 'https://fakestoreapi.com/icons/logo.png',
    twitterCard: 'summary_large_image',
    twitterTitle: () => product.value ? `${product.value.title} - LUMORA` : 'LUMORA Store',
    twitterDescription: () => product.value?.description || 'Shop fashion online in Cambodia.',
    twitterImage: () => product.value?.image || ''
})
</script>