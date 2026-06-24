<script setup>
import { ref, onMounted } from 'vue'
import MobileMenu from './AppNav/NavMobileMenu.vue'
import NavBrand from './AppNav/NavBrand.vue'
import NavLinks from './AppNav/NavLinks.vue'
import NavButons from './AppNav/NavButons.vue'
import NavCTA from './AppNav/NavCTA.vue'

const isDark = ref(false)
const mobileMenuOpen = ref(false)

const toggleMenu = () => {
    mobileMenuOpen.value = !mobileMenuOpen.value
}

const toggleDarkMode = () => {
    isDark.value = !isDark.value
    if (isDark.value) {
        document.documentElement.classList.add('dark')
    } else {
        document.documentElement.classList.remove('dark')
    }
    localStorage.setItem('theme', isDark.value ? 'dark' : 'light')
}

onMounted(() => {
    const savedTheme = localStorage.getItem('theme')
    if (
        savedTheme === 'dark' ||
        (!savedTheme && window.matchMedia('(prefers-color-scheme: dark)').matches)
    ) {
        isDark.value = true
        document.documentElement.classList.add('dark')
    } else {
        isDark.value = false
        document.documentElement.classList.remove('dark')
    }
})
</script>

<template>
    <!-- Navbar -->
    <nav
        class="fixed top-0 w-full z-50 backdrop-blur-md bg-white dark:bg-gray-950/95 border-b border-gray-200 brand-transition"
    >
        <!-- Header -->
        <div class="max-w-6xl mx-auto px-6 py-4 flex justify-between items-center">
            <!-- Brand Name -->
            <NavBrand />
            <!-- Nav buttons -->
            <NavLinks />
            <!-- Dark Mode Toggle + Mobile Menu Button + Registration Link -->
            <div class="flex items-center gap-6">
                <NavButons
                    :isDark="isDark"
                    :mobileMenuOpen="mobileMenuOpen"
                    @toggled-mode="toggleDarkMode"
                    @toggled-menu="toggleMenu"
                />
                <NavCTA />
            </div>
        </div>

        <!-- Mobile Menu -->
        <MobileMenu :mobileMenuOpen="mobileMenuOpen" @close-menu="mobileMenuOpen = false" />
    </nav>
</template>
