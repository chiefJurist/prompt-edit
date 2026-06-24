<script setup>
defineProps(['mobileMenuOpen'])
defineEmits(['closeMenu'])
</script>
<template>
    <transition
        enter-active-class="transition ease-out duration-500"
        enter-from-class="transform -translate-y-10 opacity-0"
        enter-to-class="transform translate-y-0 opacity-100"
        leave-active-class="transition ease-in duration-500"
        leave-from-class="transform translate-y-0 opacity-100"
        leave-to-class="transform -translate-y-10 opacity-0"
    >
        <div
            v-if="mobileMenuOpen"
            class="md:hidden bg-white dark:bg-gray-950 border-t border-gray-200 dark:border-gray-800 backdrop-blur-md brand-transition"
        >
            <div class="px-6 py-6 space-y-3">
                <a href="#how-it-works" @click="$emit('closeMenu')" class="mobile-menu-link"
                    >How It Works</a
                >
                <a href="#tools" @click="$emit('closeMenu')" class="mobile-menu-link">AI Tools</a>
                <a href="#templates" @click="$emit('closeMenu')" class="mobile-menu-link"
                    >Templates</a
                >
                <a href="#plugins" @click="$emit('closeMenu')" class="mobile-menu-link">Plugins</a>
                <a href="#pricing" @click="$emit('closeMenu')" class="mobile-menu-link">Pricing</a>
                <a href="#faq" @click="$emit('closeMenu')" class="mobile-menu-link">FAQ</a>
                <a
                    href="#https://promptedit.com"
                    @click="$emit('closeMenu')"
                    class="block text-xl font-semibold text-indigo-700 dark:text-indigo-600 p-2"
                    >Join Us</a
                >
            </div>
        </div>
    </transition>
</template>
