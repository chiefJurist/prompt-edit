<script setup>
import { ref } from 'vue'

const faqs = ref([
    {
        id: 1,
        question: 'What exactly is PromptEdit?',
        answer: 'Think of it as a grocery store for AI tools. Instead of subscribing to Kling, Eleven Labs, Suno, and others separately, PromptEdit gives you one login and one credit balance to use across all of them.',
    },
    {
        id: 2,
        question: "Is there a quality difference between PromptEdit and the tool's own site?",
        answer: "None at all. PromptEdit accesses the same underlying APIs as the tools' own websites. You get identical output quality on a pay-per-use basis instead of a subscription.",
    },
    {
        id: 3,
        question: 'Can I use what I create for commercial projects?',
        answer: 'Yes. Everything you generate or download during an active membership is cleared for commercial use, including advertising and client work. No additional licensing fees.',
    },
    {
        id: 4,
        question: 'What happens to my content if I cancel?',
        answer: "Any content you created and published while your account was active is covered permanently. You just won't be able to use downloaded templates in new projects after cancelling.",
    },
    {
        id: 5,
        question: 'Do credits expire?',
        answer: 'No. Credits you purchase stay in your account until you use them. No rush, no pressure.',
    },
])

const openId = ref(null)

function toggle(id) {
    openId.value = openId.value === id ? null : id
}
</script>

<template>
    <div
        id="faq"
        class="py-24 px-6 lg:px-10 bg-linear-to-br from-gray-50 via-white to-indigo-50 dark:from-gray-950 dark:via-gray-900 dark:to-indigo-950/20 transition-colors duration-1000"
    >
        <!-- Heading -->
        <div class="max-w-2xl mx-auto text-center mb-16">
            <div class="brand-text font-medium py-4">FAQ</div>
            <h2
                class="font-display text-5xl md:text-7xl font-black leading-none tracking-tight text-gray-900 dark:text-white transition-colors duration-1000"
            >
                Commonly Asked <span class="brand-text">Questions</span>
            </h2>
        </div>

        <!-- FAQ List -->
        <div
            class="max-w-3xl mx-auto divide-y divide-gray-200 dark:divide-white/10 transition-colors duration-1000"
        >
            <div v-for="faq in faqs" :key="faq.id" class="group">
                <button
                    class="w-full flex items-center justify-between gap-6 py-7 text-left cursor-pointer focus:outline-none"
                    @click="toggle(faq.id)"
                    :aria-expanded="openId === faq.id"
                >
                    <span
                        class="text-base md:text-lg font-semibold text-gray-800 dark:text-gray-100 transition-colors duration-500 group-hover:text-indigo-600 dark:group-hover:text-indigo-400"
                        :class="openId === faq.id ? 'text-indigo-600 dark:text-indigo-400' : ''"
                    >
                        {{ faq.question }}
                    </span>

                    <!-- Toggle icon -->
                    <span
                        class="shrink-0 w-8 h-8 rounded-full flex items-center justify-center border transition-all duration-500"
                        :class="
                            openId === faq.id
                                ? 'bg-indigo-600 border-indigo-600 dark:bg-indigo-500 dark:border-indigo-500'
                                : 'bg-transparent border-gray-300 dark:border-white/20 group-hover:border-indigo-400 dark:group-hover:border-indigo-600'
                        "
                    >
                        <svg
                            class="w-4 h-4 transition-all duration-500"
                            :class="
                                openId === faq.id
                                    ? 'rotate-45 text-white'
                                    : 'rotate-0 text-gray-500 dark:text-gray-400'
                            "
                            xmlns="http://www.w3.org/2000/svg"
                            viewBox="0 0 24 24"
                            fill="none"
                            stroke="currentColor"
                            stroke-width="2"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        >
                            <line x1="12" y1="5" x2="12" y2="19" />
                            <line x1="5" y1="12" x2="19" y2="12" />
                        </svg>
                    </span>
                </button>

                <!-- Answer with smooth expand -->
                <div
                    class="overflow-hidden transition-all duration-1000 ease-in-out"
                    :class="openId === faq.id ? 'max-h-64 opacity-100' : 'max-h-0 opacity-0'"
                >
                    <p
                        class="pb-7 text-sm md:text-base leading-relaxed text-gray-500 dark:text-gray-400 transition-colors duration-1000"
                    >
                        {{ faq.answer }}
                    </p>
                </div>
            </div>
        </div>
    </div>
</template>
