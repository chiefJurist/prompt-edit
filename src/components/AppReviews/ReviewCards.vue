<script setup>
import avatarHilda from '../../assets/images/Reviews/hilda-schlueter.webp'
import avatarMatt from '../../assets/images/Reviews/matt-lilley.jpg'
import avatarBrady from '../../assets/images/Reviews/brady-hales.webp'

const reviews = [
    {
        id: 1,
        initials: 'HS',
        avatar: avatarHilda,
        name: 'Hilda Schlueter',
        title: 'Online Course Creator',
        quote: 'My daughter and I got more editing work done in 3 hours than we normally do in 3 days. The asset library alone is worth every penny.',
        rating: 5,
    },
    {
        id: 2,
        initials: 'ML',
        avatar: avatarMatt,
        name: 'Matt Lilley',
        title: 'ContentCreator.com Student',
        quote: "My videos wouldn't look half as good without the Content Creator Templates Library. I lean on it heavily for every single edit I do.",
        rating: 5,
    },
    {
        id: 3,
        initials: 'BH',
        avatar: avatarBrady,
        name: 'Brady Hales',
        title: 'ContentCreator.com Student',
        quote: "A fantastic resource. I genuinely don't need any other digital asset subscription since switching to PromptEdit.",
        rating: 5,
    },
]
</script>

<template>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mt-14">
        <div
            v-for="review in reviews"
            :key="review.id"
            class="group relative rounded-2xl border p-7 flex flex-col gap-5 transition-all duration-1000 bg-white dark:bg-gray-900 border-gray-200 dark:border-white/7 shadow-sm dark:shadow-none hover:-translate-y-1.5 hover:border-indigo-300 dark:hover:border-indigo-700/60 hover:shadow-xl hover:shadow-indigo-100 dark:hover:shadow-indigo-950/60"
        >
            <!-- Stars -->
            <div class="flex items-center gap-0.5">
                <svg
                    v-for="n in review.rating"
                    :key="n"
                    class="w-4 h-4 text-indigo-500 dark:text-indigo-400 transition-colors duration-500"
                    viewBox="0 0 20 20"
                    fill="currentColor"
                    xmlns="http://www.w3.org/2000/svg"
                >
                    <path
                        d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"
                    />
                </svg>
            </div>

            <!-- Quote -->
            <p
                class="text-sm leading-relaxed text-gray-600 dark:text-gray-300 flex-1 transition-colors duration-1000"
            >
                "{{ review.quote }}"
            </p>

            <!-- Divider -->
            <div
                class="h-px bg-gray-100 dark:bg-white/7 group-hover:bg-indigo-100 dark:group-hover:bg-indigo-800/30 transition-colors duration-1000"
            />

            <!-- Author -->
            <div class="flex items-center gap-3">
                <!-- Avatar -->
                <div
                    class="w-10 h-10 rounded-full shrink-0 overflow-hidden border transition-all duration-500 border-gray-200 dark:border-white/10 group-hover:border-indigo-300 dark:group-hover:border-indigo-700/50 group-hover:shadow-md group-hover:shadow-indigo-200 dark:group-hover:shadow-indigo-900"
                >
                    <img
                        :src="review.avatar"
                        :alt="review.name"
                        class="w-full h-full object-cover"
                        @error="(e) => (e.target.style.display = 'none')"
                    />
                    <!-- Fallback initials — shown if image fails to load -->
                    <div
                        class="w-full h-full flex items-center justify-center text-xs font-bold bg-indigo-100 dark:bg-indigo-900/40 text-indigo-600 dark:text-indigo-400"
                    >
                        {{ review.initials }}
                    </div>
                </div>

                <!-- Name & title -->
                <div>
                    <div
                        class="text-sm font-semibold text-gray-900 dark:text-gray-50 transition-colors duration-1000"
                    >
                        {{ review.name }}
                    </div>
                    <div
                        class="text-xs text-gray-400 dark:text-gray-500 transition-colors duration-1000"
                    >
                        {{ review.title }}
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
