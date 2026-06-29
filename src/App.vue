<script setup>
import AppFAQ from './components/AppFAQ.vue'
import AppFooter from './components/AppFooter.vue'
import AppGuide from './components/AppGuide.vue'
import AppHero from './components/AppHero.vue'
import AppNav from './components/AppNav.vue'
import AppPricing from './components/AppPricing.vue'
import AppReview from './components/AppReview.vue'
import AppTemplate from './components/AppTemplate.vue'
import AppTools from './components/AppTools.vue'
</script>

<template>
    <div class="bg-gray-50 text-gray-800 dark:bg-gray-950 dark:text-white">
        <AppNav />
        <AppHero />
        <AppGuide />
        <AppTools />
        <AppTemplate />
        <AppPricing />
        <AppReview />
        <AppFAQ />
        <AppFooter />
    </div>
</template>
