<template>
    <div class="max-w-2xl mx-auto mt-32">
        <div
            class="rounded-2xl border p-10 md:p-14 flex flex-col items-center text-center gap-6 transition-colors duration-1000 bg-white dark:bg-gray-900 border-gray-200 dark:border-white/7 shadow-sm dark:shadow-none"
        >
            <!-- Shield icon -->
            <div
                class="w-16 h-16 rounded-full flex items-center justify-center transition-all duration-500 bg-indigo-100 dark:bg-indigo-900/30 border border-indigo-200 dark:border-indigo-700/40 shadow-md shadow-indigo-100 dark:shadow-indigo-950/50"
            >
                <svg
                    class="w-7 h-7 text-indigo-600 dark:text-indigo-400 transition-colors duration-500"
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 24 24"
                    fill="none"
                    stroke="currentColor"
                    stroke-width="1.6"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                >
                    <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z" />
                    <path d="M9 12l2 2 4-4" />
                </svg>
            </div>

            <!-- Headline -->
            <h2
                class="font-display font-black text-3xl md:text-4xl leading-tight tracking-tight text-gray-900 dark:text-gray-50 transition-colors duration-1000"
            >
                30-day money-back <span class="brand-text">guarantee</span>
            </h2>

            <!-- Divider -->
            <div
                class="w-12 h-px bg-indigo-200 dark:bg-indigo-800/50 transition-colors duration-1000"
            />

            <!-- Body copy -->
            <p
                class="text-base leading-relaxed text-gray-500 dark:text-gray-400 max-w-lg transition-colors duration-1000"
            >
                If PromptEdit isn't right for you, email us within 30 days and we'll refund your
                purchase no questions asked. <br />
                Spent credits are non-refundable (think of them like gas, once you've driven
                somewhere, you can't return the fuel), but everything else is fully covered.
            </p>
        </div>
    </div>
</template>
