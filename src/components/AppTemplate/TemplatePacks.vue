<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

import imgA from '../../assets/images/text-pack-template.png'
import imgB from '../../assets/images/text-pack-template-2.webp'
import imgC from '../../assets/images/overlay-pack-template.png'
import imgD from '../../assets/images/overlay-pack-template-2.webp'
import imgE from '../../assets/images/background-pack-template.webp'
import imgF from '../../assets/images/background-pack-template-2.webp'

const images = ref([
    { id: 1, name: 'TEXT PACK', url: imgA },
    { id: 2, name: 'ANIMATED TEXT', url: imgB },
    { id: 3, name: 'OVERLAY PACK', url: imgC },
    { id: 4, name: 'ANIMATED OVERLAY', url: imgD },
    { id: 5, name: 'BACKGROUND PACK', url: imgE },
    { id: 6, name: 'ANIMATED BACKGROUND', url: imgF },
])

const currentIndex = ref(0)
const isTransitioning = ref(false)
let intervalId = null

function nextSlide() {
    if (isTransitioning.value) return
    isTransitioning.value = true
    setTimeout(() => {
        currentIndex.value = (currentIndex.value + 1) % images.value.length
        isTransitioning.value = false
    }, 400)
}

function goToSlide(i) {
    if (i === currentIndex.value) return
    clearInterval(intervalId)
    currentIndex.value = i
    intervalId = setInterval(nextSlide, 5000)
}

onMounted(() => {
    intervalId = setInterval(nextSlide, 5000)
})

onUnmounted(() => {
    clearInterval(intervalId)
})
</script>

<template>
    <div
        class="my-20 max-w-4xl mx-auto group relative rounded-2xl overflow-hidden border border-gray-200 dark:border-white/7 bg-white dark:bg-gray-900 shadow-sm dark:shadow-none transition-all duration-500 ease-out hover:shadow-xl hover:border-indigo-300 dark:hover:border-indigo-700/60 dark:hover:shadow-xl"
    >
        <!-- ── Image Slideshow ── -->
        <div class="relative w-full aspect-video bg-gray-100 dark:bg-gray-700 overflow-hidden">
            <transition name="slide-morph" mode="out-in">
                <div :key="images[currentIndex].id" class="absolute inset-0 overflow-hidden">
                    <img
                        :src="images[currentIndex].url"
                        :alt="images[currentIndex].name"
                        class="w-full h-full object-cover transition-transform duration-500 ease-in-out"
                    />

                    <!-- Name badge — bottom-left -->
                    <div
                        class="absolute bottom-2.5 left-3 flex items-center gap-1.5 bg-black/60 backdrop-blur-md border border-white/10 rounded-full px-3 py-2 pointer-events-none"
                    >
                        <span
                            class="w-1.5 h-1.5 rounded-full bg-indigo-400 dark:bg-indigo-400 shrink-0 shadow-sm shadow-indigo-400"
                        />
                        <span
                            class="text-xs font-medium text-white/90 tracking-wide whitespace-nowrap"
                        >
                            {{ images[currentIndex].name }}
                        </span>
                    </div>
                </div>
            </transition>

            <!-- Slide indicators — bottom-right -->
            <div class="absolute bottom-2.5 right-3 flex items-center gap-1.5">
                <button
                    v-for="(img, i) in images"
                    :key="img.id"
                    :aria-label="`Go to slide ${i + 1}`"
                    @click="goToSlide(i)"
                    class="w-1.5 h-1.5 rounded-full border-0 p-0 cursor-pointer transition-all duration-500"
                    :class="
                        i === currentIndex
                            ? 'bg-indigo-400 scale-125 shadow-sm shadow-indigo-400'
                            : 'bg-white/30 hover:bg-white/60'
                    "
                />
            </div>
        </div>

        <!-- ── Card Body ── -->
        <div class="flex flex-col gap-2.5 p-5">
            <!-- Title -->
            <h3 class="text-2xl font-bold leading-snug text-gray-900 dark:text-gray-50 py-5">
                Plug-and-Play Template Packs for Every Kind of Creator
            </h3>

            <!-- Description -->
            <p class="leading-relaxed text-gray-500 dark:text-gray-400 text-lg">
                Stop starting from scratch. Each pack in the Content Creator Template Library is a
                hand-curated collection of production-ready templates built around a specific
                creative workflow. <br />
                Every template is optimized for the best AI tool available today, so you're not just
                getting a starting point, you're getting a proven system. <br />
                Pick your pack, load your tools, and go from blank page to finished content in a
                fraction of the time.
            </p>
        </div>
    </div>
</template>

<style scoped>
/* Vue transition states for the blur-fade-drift effect */
.slide-morph-enter-active {
    transition:
        opacity 0.45s ease,
        filter 0.45s ease,
        transform 0.45s cubic-bezier(0.22, 1, 0.36, 1);
}
.slide-morph-leave-active {
    transition:
        opacity 0.35s ease,
        filter 0.35s ease,
        transform 0.35s ease;
}
.slide-morph-enter-from {
    opacity: 0;
    filter: blur(8px) brightness(1.3);
    transform: scale(1.04);
}
.slide-morph-leave-to {
    opacity: 0;
    filter: blur(6px) brightness(0.7);
    transform: scale(0.97);
}

@media (prefers-reduced-motion: reduce) {
    .slide-morph-enter-active,
    .slide-morph-leave-active {
        transition: none !important;
    }
}
</style>
