<script setup lang="ts">
import GuideCards from './AppGuide/GuideCards.vue'
import GuideText from './AppGuide/GuideText.vue'
</script>

<template>
    <div
        id="how-it-works"
        class="py-36 px-6 lg:px-10 bg-linear-to-br from-gray-50 via-white to-indigo-50 dark:from-gray-950 dark:via-gray-900 dark:to-indigo-950/20 transition-color duration-500"
    >
        <GuideText />
        <GuideCards />
    </div>
</template>
