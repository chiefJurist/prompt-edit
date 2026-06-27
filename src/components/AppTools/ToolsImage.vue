<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

import imgA from '../../assets/Videos/VideoTools/clone-videos.mp4'
import imgB from '../../assets/Videos/VideoTools/visual-effects.mp4'
import imgC from '../../assets/Videos/VideoTools/cinematic-videos.mp4'
import imgD from '../../assets/Videos/VideoTools/video-ads.mp4'
import imgE from '../../assets/Videos/VideoTools/reels-&-tiktok.mp4'
import imgF from '../../assets/Videos/VideoTools/youtube-videos.mp4'

const images = ref([
    { id: 1, name: 'Clone Videos', url: imgA },
    { id: 2, name: 'Visual Effects', url: imgB },
    { id: 3, name: 'Cinematic Films', url: imgC },
    { id: 4, name: 'Video Ads', url: imgD },
    { id: 5, name: 'Reels & tiktok', url: imgE },
    { id: 6, name: 'Youtube Videos', url: imgF },
])

const tools = ref([{ label: 'Veo' }, { label: 'Kling AI' }, { label: 'Seedance' }])

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
    intervalId = setInterval(nextSlide, 3500)
}

onMounted(() => {
    intervalId = setInterval(nextSlide, 3500)
})

onUnmounted(() => {
    clearInterval(intervalId)
})
</script>

<template>
    <div
        class="group relative w-full max-w-sm rounded-2xl overflow-hidden cursor-pointer border border-gray-200 dark:border-white/7 bg-white dark:bg-gray-900 shadow-sm dark:shadow-none transition-all duration-500 ease-out hover:-translate-y-1.5 hover:scale-105 hover:shadow-xl hover:border-indigo-300 dark:hover:border-indigo-700/60 dark:hover:shadow-2xl"
    >
        <!-- ── Image Slideshow ── -->
        <div class="relative w-full aspect-video bg-gray-100 dark:bg-gray-950 overflow-hidden">
            <transition name="slide-morph" mode="out-in">
                <div :key="images[currentIndex].id" class="absolute inset-0 overflow-hidden">
                    <img
                        :src="images[currentIndex].url"
                        :alt="images[currentIndex].name"
                        class="w-full h-full object-cover transition-transform duration-500 ease-in-out group-hover:scale-105"
                    />

                    <!-- Name badge — bottom-left -->
                    <div
                        class="absolute bottom-2.5 left-3 flex items-center gap-1.5 bg-black/60 backdrop-blur-md border border-white/10 rounded-full px-2.5 py-1 pointer-events-none"
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
            <!-- Icon -->
            <div
                class="w-11 h-11 rounded-xl flex items-center justify-center text-indigo-700 dark:text-indigo-400 bg-indigo-100 dark:bg-indigo-900/30 border border-indigo-200 dark:border-indigo-700/40 transition-all duration-500 group-hover:bg-indigo-200 dark:group-hover:bg-indigo-800/40 group-hover:shadow-md group-hover:shadow-indigo-200 dark:group-hover:shadow-indigo-900"
            >
                <svg
                    class="w-5 h-5"
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 24 24"
                    fill="none"
                    stroke="currentColor"
                    stroke-width="1.6"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                >
                    <polygon points="23 7 16 12 23 17 23 7" />
                    <rect x="1" y="5" width="15" height="14" rx="2" ry="2" />
                </svg>
            </div>

            <!-- Title -->
            <h3 class="text-base font-bold leading-snug text-gray-900 dark:text-gray-50">
                AI Video Generation
            </h3>

            <!-- Description -->
            <p class="text-sm leading-relaxed text-gray-500 dark:text-gray-400">
                Generate cinematic clips, visual effects, and social-ready videos from text or image
                prompts.
            </p>

            <!-- Tool tags -->
            <div class="flex flex-wrap gap-1.5 mt-1">
                <span
                    v-for="tool in tools"
                    :key="tool.label"
                    class="text-xs font-medium px-2.5 py-0.5 rounded-md border border-gray-200 dark:border-white/10 text-gray-600 dark:text-gray-400 bg-gray-100 dark:bg-white/5 transition-all duration-500 group-hover:border-indigo-300 dark:group-hover:border-indigo-700/50 group-hover:text-indigo-700 dark:group-hover:text-indigo-400 group-hover:bg-indigo-50 dark:group-hover:bg-indigo-900/20"
                >
                    {{ tool.label }}
                </span>
            </div>
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
