<script setup>
import PricingCards from './AppPricing/PricingCards.vue'
import PricingGuarantee from './AppPricing/PricingGuarantee.vue'
import PricingIntro from './AppPricing/PricingIntro.vue'
</script>

<template>
    <div
        id="pricing"
        class="py-36 px-6 lg:px-10 bg-linear-to-br from-gray-50 via-white to-indigo-50 dark:from-gray-950 dark:via-gray-900 dark:to-indigo-950/20 transition-colors duration-1000"
    >
        <PricingIntro />
        <PricingCards />
        <PricingGuarantee />
    </div>
</template>
