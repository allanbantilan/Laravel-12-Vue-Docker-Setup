<script setup>
import { Link } from "@inertiajs/vue3";

const props = defineProps({
    canRegister: {
        type: Boolean,
    },
    stats: {
        type: Array,
        default: () => [
            { value: "10K+", label: "Happy Users" },
            { value: "99.9%", label: "Uptime" },
            { value: "24/7", label: "Support" },
            { value: "50+", label: "Countries" },
        ],
    },
});

const emit = defineEmits(["scroll-to-features"]);
</script>

<template>
    <section class="pt-32 pb-20 px-4 sm:px-6 lg:px-8 relative overflow-hidden">
        <!-- Background Decoration -->
        <div class="absolute inset-0 overflow-hidden">
            <div
                class="absolute -top-40 -right-40 w-80 h-80 bg-blue-100 dark:bg-blue-900/20 rounded-full mix-blend-multiply filter blur-3xl opacity-70"
            ></div>
            <div
                class="absolute -bottom-40 -left-40 w-80 h-80 bg-indigo-100 dark:bg-indigo-900/20 rounded-full mix-blend-multiply filter blur-3xl opacity-70"
            ></div>
        </div>

        <div class="max-w-7xl mx-auto relative">
            <div class="text-center">
                <h1
                    class="text-5xl md:text-7xl font-bold text-gray-900 dark:text-white mb-6 leading-tight"
                >
                    Template
                    <span
                        class="bg-gradient-to-r from-blue-600 to-indigo-600 bg-clip-text text-transparent"
                    >
                        Only
                    </span>
                </h1>
                <p
                    class="text-xl text-gray-600 dark:text-gray-300 mb-10 max-w-3xl mx-auto"
                >
                    Transform your ideas into reality with our powerful
                    platform. Join thousands of creators building the next
                    generation of digital products.
                </p>
                <div class="flex flex-col sm:flex-row gap-4 justify-center">
                    <Link
                        v-if="canRegister"
                        :href="route('register')"
                        class="px-8 py-4 bg-gradient-to-r from-blue-600 to-indigo-600 hover:from-blue-700 hover:to-indigo-700 text-white rounded-xl font-semibold text-lg shadow-lg hover:shadow-xl transform hover:-translate-y-1 transition-all duration-300"
                    >
                        Start Free Trial
                    </Link>
                    <button
                        @click="$emit('scroll-to-features')"
                        class="px-8 py-4 bg-white dark:bg-gray-800 hover:bg-gray-50 dark:hover:bg-gray-700 text-gray-900 dark:text-white border border-gray-300 dark:border-gray-600 rounded-xl font-semibold text-lg shadow-md hover:shadow-lg transition-all duration-300"
                    >
                        Learn More
                    </button>
                </div>
            </div>

            <!-- Stats -->
            <div
                class="mt-20 grid grid-cols-2 md:grid-cols-4 gap-6 max-w-4xl mx-auto"
            >
                <div
                    v-for="(stat, index) in stats"
                    :key="index"
                    class="text-center"
                >
                    <div
                        class="text-3xl md:text-4xl font-bold text-gray-900 dark:text-white mb-2"
                    >
                        {{ stat.value }}
                    </div>
                    <div class="text-gray-600 dark:text-gray-400">
                        {{ stat.label }}
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>
