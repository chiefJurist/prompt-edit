<script setup>
import { ref, onMounted } from 'vue'
import vidA from '../../assets/Videos/tools-plugins.mp4'

const video = ref({ id: 1, name: 'AI Editing Plugins', url: vidA })
const tools = ref([{ label: 'Adobe Premier Pro' }, { label: 'Davinci Resolve' }])
const videoRef = ref(null)

onMounted(() => {
    if (videoRef.value) {
        videoRef.value.play()
    }
})
</script>

<template>
    <div
        class="group relative w-full max-w-sm rounded-2xl overflow-hidden cursor-pointer border border-gray-200 dark:border-white/[0.07] bg-white dark:bg-gray-900 shadow-sm dark:shadow-none transition-all duration-500 ease-out hover:-translate-y-1.5 hover:scale-105 hover:shadow-xl hover:border-indigo-300 dark:hover:border-indigo-700/60 dark:hover:shadow-2xl dark:hover:shadow-black/50"
    >
        <!-- ── Video Slideshow ── -->
        <div class="relative w-full aspect-video bg-gray-100 dark:bg-gray-950 overflow-hidden">
            <transition name="slide-morph" mode="out-in">
                <div :key="video.id" class="absolute inset-0 overflow-hidden">
                    <video
                        ref="videoRef"
                        :src="video.url"
                        :alt="video.name"
                        class="w-full h-full object-cover transition-transform duration-500 ease-in-out group-hover:scale-105"
                        muted
                        playsinline
                        autoplay
                        loop
                        @ended="onVideoEnded"
                    />

                    <!-- Name badge — bottom-left -->
                    <div
                        class="absolute bottom-2.5 left-3 flex items-center gap-1.5 bg-black/60 backdrop-blur-md border border-white/10 rounded-full px-2.5 py-1 pointer-events-none"
                    >
                        <span
                            class="w-1.5 h-1.5 rounded-full bg-indigo-400 shrink-0 shadow-sm shadow-indigo-400"
                        />
                        <span
                            class="text-xs font-medium text-white/90 tracking-wide whitespace-nowrap"
                        >
                            {{ video.name }}
                        </span>
                    </div>
                </div>
            </transition>

            <!-- Slide indicators — bottom-right -->
            <div class="absolute bottom-2.5 right-3 flex items-center gap-1.5">
                <button
                    class="w-1.5 h-1.5 rounded-full border-0 p-0 cursor-pointer transition-all duration-300 bg-indigo-400 scale-125 shadow-sm shadow-indigo-400"
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
                    <rect x="5" y="5" width="14" height="14" rx="1.5" />
                    <circle cx="12" cy="5" r="2.5" />
                    <circle cx="12" cy="19" r="2.5" />
                    <circle cx="5" cy="12" r="2.5" />
                    <circle cx="19" cy="12" r="2.5" />
                </svg>
            </div>

            <!-- Title -->
            <h3 class="text-base font-bold leading-snug text-gray-900 dark:text-gray-50">
                Editing Plugins
            </h3>

            <!-- Description -->
            <p class="text-sm leading-relaxed text-gray-500 dark:text-gray-400">
                AI tools that live inside DaVinci Resolve and Adobe Premiere.<br />
                No browser switching needed.
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
