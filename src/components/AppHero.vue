<script setup lang="ts">
import HeroBody from './AppHero/HeroBody.vue'
import HeroCards from './AppHero/HeroCards.vue'
import HeroRating from './AppHero/HeroRating.vue'
import HeroTag from './AppHero/HeroTag.vue'
</script>

<template>
    <div
        class="py-36 px-6 lg:px-10 bg-linear-to-br from-gray-50 via-white to-indigo-50 dark:from-gray-950 dark:via-gray-900 dark:to-indigo-950/20 transition-color duration-500"
    >
        <div class="max-w-4xl mx-auto">
            <!-- Hero Tag-->
            <HeroTag />

            <!-- Hero Body -->
            <HeroBody />

            <!-- Hero Rating -->
            <HeroRating />

            <!-- Hero Cards -->
            <HeroCards />
        </div>
    </div>
</template>
