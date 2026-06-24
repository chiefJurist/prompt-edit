<script setup>
import { ref } from 'vue'

const stats = ref([
    { statAmount: '20+', statDetail: 'AI tools in one place' },
    { statAmount: '100k+', statDetail: 'Editing templates' },
    { statAmount: '$0', statDetail: 'Monthly minimum' },
    { statAmount: '50k+', statDetail: 'Active creators' },
])
</script>

<template>
    <div class="grid grid-cols-1 md:grid-cols-4 gap-2">
        <div
            v-for="stat in stats"
            :key="stat.statAmount"
            class="bg-indigo-100/90 dark:bg-indigo-950/90 border border-stone-100 shadow px-8 py-5 rounded-lg brand-transition"
        >
            <div class="font-display font-black brand-text text-5xl text-center">
                {{ stat.statAmount }}
            </div>
            <div class="text-center font-medium my-2">{{ stat.statDetail }}</div>
        </div>
    </div>
</template>
