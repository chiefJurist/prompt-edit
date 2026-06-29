<script setup>
const plans = [
    {
        id: 'payg',
        label: 'Pay as you go',
        price: 98,
        period: 'one-time — get $110 in credits',
        featured: false,
        badge: null,
        features: [
            { text: '$110 worth of AI credits', highlight: true },
            { text: 'Use on any tool, any time', highlight: false },
            { text: 'Top up whenever you need', highlight: false },
            { text: 'Commercial license included', highlight: false },
            { text: 'Credits never expire', highlight: false },
        ],
        cta: 'Get credits',
    },
    {
        id: 'monthly',
        label: 'Monthly subscription',
        price: 39,
        period: 'per month — cancel any time',
        featured: true,
        badge: 'Most popular',
        features: [
            { text: '$49/month in AI credits', highlight: true },
            { text: '100,000+ editing templates', highlight: true },
            { text: '20% bonus on extra credit purchases', highlight: true },
            { text: 'Priority generation speeds', highlight: false },
            { text: 'Run multiple generations at once', highlight: false },
            { text: 'Commercial license included', highlight: false },
        ],
        cta: 'Start free trial',
    },
]
</script>

<template>
    <div class="grid grid-cols-1 md:grid-cols-2 gap-6 max-w-3xl mx-auto mt-14">
        <div
            v-for="plan in plans"
            :key="plan.id"
            class="relative rounded-2xl border p-8 flex flex-col gap-6 transition-all duration-1000"
            :class="
                plan.featured
                    ? 'bg-indigo-50 dark:bg-indigo-950/40 border-indigo-300 dark:border-indigo-700/60 shadow-xl shadow-indigo-100 dark:shadow-indigo-950/60'
                    : 'bg-white dark:bg-gray-900 border-gray-200 dark:border-white/7 shadow-sm dark:shadow-none'
            "
        >
            <!-- Badge -->
            <div
                v-if="plan.badge"
                class="absolute -top-3.5 left-1/2 -translate-x-1/2 px-4 py-1 rounded-full text-xs font-bold uppercase tracking-widest bg-indigo-600 text-white shadow-md shadow-indigo-400/30 transition-colors duration-500"
            >
                {{ plan.badge }}
            </div>

            <!-- Plan label -->
            <div
                class="text-xs font-semibold uppercase tracking-widest transition-colors duration-1000"
                :class="
                    plan.featured
                        ? 'text-indigo-500 dark:text-indigo-400'
                        : 'text-gray-400 dark:text-gray-500'
                "
            >
                {{ plan.label }}
            </div>

            <!-- Price block -->
            <div class="flex flex-col gap-1">
                <div
                    class="font-display font-black leading-none tracking-tight transition-colors duration-1000"
                    :class="
                        plan.featured
                            ? 'text-indigo-700 dark:text-indigo-300'
                            : 'text-gray-900 dark:text-gray-50'
                    "
                >
                    <span class="text-2xl align-top mt-2 inline-block font-semibold">$</span>
                    <span class="text-6xl">{{ plan.price }}</span>
                </div>
                <p
                    class="text-sm transition-colors duration-1000"
                    :class="
                        plan.featured
                            ? 'text-indigo-400 dark:text-indigo-500'
                            : 'text-gray-400 dark:text-gray-500'
                    "
                >
                    {{ plan.period }}
                </p>
            </div>

            <!-- Divider -->
            <div
                class="h-px transition-colors duration-1000"
                :class="
                    plan.featured
                        ? 'bg-indigo-200 dark:bg-indigo-800/50'
                        : 'bg-gray-100 dark:bg-white/7'
                "
            />

            <!-- Features -->
            <ul class="flex flex-col gap-3 flex-1">
                <li
                    v-for="feature in plan.features"
                    :key="feature.text"
                    class="flex items-start gap-3 text-sm leading-relaxed transition-colors duration-1000"
                    :class="
                        feature.highlight
                            ? plan.featured
                                ? 'text-indigo-800 dark:text-indigo-200 font-medium'
                                : 'text-gray-900 dark:text-gray-100 font-medium'
                            : 'text-gray-500 dark:text-gray-400'
                    "
                >
                    <!-- Check icon -->
                    <span
                        class="mt-0.5 shrink-0 w-4 h-4 rounded-full flex items-center justify-center transition-colors duration-500"
                        :class="
                            plan.featured
                                ? 'bg-indigo-100 dark:bg-indigo-900/50'
                                : 'bg-gray-100 dark:bg-white/5'
                        "
                    >
                        <svg
                            class="w-2.5 h-2.5 transition-colors duration-500"
                            :class="
                                plan.featured
                                    ? 'text-indigo-500 dark:text-indigo-400'
                                    : 'text-gray-400 dark:text-gray-500'
                            "
                            viewBox="0 0 10 10"
                            fill="none"
                            xmlns="http://www.w3.org/2000/svg"
                        >
                            <path
                                d="M2 5l2 2 4-4"
                                stroke="currentColor"
                                stroke-width="1.5"
                                stroke-linecap="round"
                                stroke-linejoin="round"
                            />
                        </svg>
                    </span>
                    {{ feature.text }}
                </li>
            </ul>

            <!-- CTA -->
            <a
                href="https://promptedit.com"
                class="block text-center py-3.5 rounded-xl font-semibold text-sm tracking-wide transition-all duration-500"
                :class="
                    plan.featured
                        ? 'bg-indigo-600 hover:bg-indigo-500 text-white shadow-md shadow-indigo-400/30 hover:shadow-indigo-400/50 hover:-translate-y-0.5'
                        : 'bg-gray-100 hover:bg-gray-200 dark:bg-white/5 dark:hover:bg-white/10 text-gray-700 dark:text-gray-300 border border-gray-200 dark:border-white/10 hover:border-indigo-300 dark:hover:border-indigo-700/50'
                "
            >
                {{ plan.cta }}
            </a>
        </div>
    </div>
</template>
