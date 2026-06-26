<script setup>
import { ref } from 'vue'

const steps = ref([
    {
        stepNumber: '01',
        stepHeading: 'Buy credits once',
        stepBody:
            'Purchase a credit pack. No recurring charge, no commitment. Credits never expire.',
    },
    {
        stepNumber: '02',
        stepHeading: 'Pick any tool',
        stepBody: 'Browse Veo, Kling, Eleven Labs, Suno, Ideogram, and 15+ more. Swap freely.',
    },
    {
        stepNumber: '03',
        stepHeading: 'Generate instantly',
        stepBody: 'One login, one interface. No jumping between sites or learning new dashboards.',
    },
    {
        stepNumber: '04',
        stepHeading: 'Keep everything',
        stepBody: 'All content you create is commercially yours forever. No license expiry.',
    },
])
</script>

<template>
    <div class="grid grid-cols-1 md:grid-cols-4 gap-2 my-10">
        <div
            v-for="step in steps"
            :key="step.stepNumber"
            class="bg-indigo-50/70 dark:bg-indigo-950/70 border border-stone-100 dark:border-stone-800 shadow px-8 py-5 rounded-lg brand-transition"
        >
            <div
                class="font-display font-black text-5xl md:text-7xl text-indigo-200 dark:text-indigo-800 text-center"
            >
                {{ step.stepNumber }}
            </div>
            <div class="text-center font-medium py-2">{{ step.stepHeading }}</div>
            <div class="text-center font-light text-gray-600 dark:text-gray-400 py-2">
                {{ step.stepBody }}
            </div>
        </div>
    </div>
</template>
