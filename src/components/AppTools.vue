<script setup>
import ToolsAudio from './AppTools/ToolsAudioCard.vue'
import ToolsImage from './AppTools/ToolsImageCard.vue'
import ToolsIntro from './AppTools/ToolsIntro.vue'
import ToolsVideo from './AppTools/ToolsVideoCard.vue'
</script>

<template>
    <div
        id="tools"
        class="py-36 px-6 lg:px-10 bg-linear-to-br from-gray-50 via-white to-indigo-50 dark:from-gray-950 dark:via-gray-900 dark:to-indigo-950/20 transition-colors duration-1000"
    >
        <!-- Tools Intro -->
        <ToolsIntro />

        <!-- Tools Cards -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8 my-10">
            <ToolsVideo />
            <ToolsImage />
            <ToolsAudio />
        </div>
    </div>
</template>
