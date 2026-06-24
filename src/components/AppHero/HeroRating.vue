<template>
    <div class="flex flex-col md:flex-row gap-5 justify-center items-center my-20">
        <div class="text-sm text-indigo-900 dark:text-indigo-700 font-medium">
            Trusted by 50,000+ creators worldwide
        </div>
        <div class="flex items-center gap-2">
            <div class="flex items-center gap-0.5">
                <!-- 4 full stars -->
                <svg
                    v-for="n in 4"
                    :key="n"
                    class="w-5 h-5 text-yellow-400"
                    viewBox="0 0 24 24"
                    fill="currentColor"
                >
                    <polygon
                        points="12,2 15.09,8.26 22,9.27 17,14.14 18.18,21.02 12,17.77 5.82,21.02 7,14.14 2,9.27 8.91,8.26"
                    />
                </svg>
                <!-- 5th star: 90% filled -->
                <svg class="w-5 h-5" viewBox="0 0 24 24">
                    <defs>
                        <linearGradient id="partial">
                            <stop offset="70%" stop-color="#FACC15" />
                            <stop offset="70%" stop-color="#D1D5DB" />
                        </linearGradient>
                    </defs>
                    <polygon
                        points="12,2 15.09,8.26 22,9.27 17,14.14 18.18,21.02 12,17.77 5.82,21.02 7,14.14 2,9.27 8.91,8.26"
                        fill="url(#partial)"
                    />
                </svg>
            </div>
            <span class="text-sm font-semibold text-gray-900 dark:text-white">4.9</span>
            <span class="text-sm text-gray-500 dark:text-gray-400">(2,341 reviews)</span>
        </div>
    </div>
</template>
