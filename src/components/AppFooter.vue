<script setup>
const links = [
    { label: 'Terms', href: 'https://www.contentcreator.com/terms-and-conditions' },
    { label: 'Privacy', href: 'https://www.contentcreator.com/privacy-policy' },
    { label: 'Support', href: 'mailto:support@contentcreator.com' },
]
</script>

<template>
    <footer
        class="border-t border-gray-200 dark:border-white/10 bg-white dark:bg-gray-950 transition-colors duration-1000"
    >
        <div class="max-w-7xl mx-auto px-6 lg:px-10 py-6 flex flex-col gap-10">
            <div
                class="flex flex-col sm:flex-row items-start sm:items-center justify-between gap-6"
            >
                <!-- Logo -->
                <div
                    class="font-display font-black text-2xl tracking-tight text-gray-900 dark:text-white transition-colors duration-1000"
                >
                    Prompt<span class="brand-text">Edit</span>
                </div>

                <!-- Legal Links -->
                <div class="flex items-center gap-6">
                    <a
                        v-for="link in links"
                        :key="link.label"
                        :href="link.href"
                        class="text-xs text-gray-600 dark:text-gray-400 hover:text-indigo-600 dark:hover:text-indigo-400 transition-colors duration-500"
                    >
                        {{ link.label }}
                    </a>
                </div>

                <!-- Copy Right -->
                <p class="text-xs text-gray-600 dark:text-gray-400 transition-colors duration-1000">
                    © {{ new Date().getFullYear() }} Paul Xavier International LLC
                </p>
            </div>
        </div>
    </footer>
</template>
