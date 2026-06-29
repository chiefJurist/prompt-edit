<script setup>
import PricingCards from './AppPricing/PricingCards.vue'
import PricingGuarantee from './AppPricing/PricingGuarantee.vue'
import PricingIntro from './AppPricing/PricingIntro.vue'
</script>

<template>
    <div
        id="pricing"
        class="py-36 px-6 lg:px-10 bg-linear-to-br from-white via-indigo-50/30 to-white dark:from-gray-950 dark:via-indigo-950/10 dark:to-gray-950 transition-colors duration-1000"
    >
        <PricingIntro />
        <PricingCards />
        <PricingGuarantee />
    </div>
</template>
