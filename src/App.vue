<script setup>
import AppGuide from './components/AppGuide.vue'
import AppHero from './components/AppHero.vue'
import AppNav from './components/AppNav.vue'
import AppTools from './components/AppTools.vue'
</script>

<template>
    <div class="bg-gray-50 text-gray-800 dark:bg-gray-950 dark:text-white">
        <AppNav />
        <AppHero />
        <AppGuide />
        <AppTools />
    </div>
</template>
