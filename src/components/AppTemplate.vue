<script setup>
import TemplateIntro from './AppTemplate/TemplateIntro.vue'
import TemplatePacks from './AppTemplate/TemplatePacks.vue'
</script>

<template>
    <div
        id="templates"
        class="py-36 px-6 lg:px-10 bg-linear-to-br from-gray-50 via-white to-indigo-50 dark:from-gray-950 dark:via-gray-900 dark:to-indigo-950/20 transition-colors duration-1000"
    >
        <TemplateIntro />
        <TemplatePacks />
    </div>
</template>
