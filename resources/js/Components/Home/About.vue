<script setup>
const stats = [
    { value: "50+", label: "Team Members", color: "blue" },
    { value: "5+", label: "Years Experience", color: "green" },
    { value: "100+", label: "Countries Served", color: "purple" },
    { value: "24/7", label: "Support Available", color: "orange" },
];

const features = [
    "Industry-leading technology",
    "24/7 customer support",
    "Global infrastructure",
];
</script>

<template>
    <section id="about" class="py-20 px-4 sm:px-6 lg:px-8">
        <div class="max-w-7xl mx-auto">
            <div class="grid lg:grid-cols-2 gap-12 items-center">
                <div>
                    <h2
                        class="text-4xl md:text-5xl font-bold text-gray-900 dark:text-white mb-6"
                    >
                        About Our Company
                    </h2>
                    <p class="text-lg text-gray-600 dark:text-gray-300 mb-6">
                        Founded in 2020, we're on a mission to democratize
                        digital creation. We believe that anyone, anywhere,
                        should be able to build amazing digital experiences
                        without needing to be a technical expert.
                    </p>
                    <p class="text-lg text-gray-600 dark:text-gray-300 mb-8">
                        Our team of passionate engineers, designers, and product
                        specialists work tirelessly to create tools that empower
                        creators, entrepreneurs, and businesses of all sizes.
                    </p>
                    <div class="flex flex-wrap gap-4">
                        <div
                            v-for="(feature, index) in features"
                            :key="index"
                            class="flex items-center space-x-2 text-gray-700 dark:text-gray-300"
                        >
                            <svg
                                class="w-5 h-5 text-green-500"
                                fill="none"
                                stroke="currentColor"
                                viewBox="0 0 24 24"
                            >
                                <path
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                    stroke-width="2"
                                    d="M5 13l4 4L19 7"
                                />
                            </svg>
                            <span>{{ feature }}</span>
                        </div>
                    </div>
                </div>
                <div class="relative">
                    <div
                        class="bg-gradient-to-br from-blue-500 to-indigo-600 rounded-3xl p-1"
                    >
                        <div class="bg-white dark:bg-gray-800 rounded-2xl p-8">
                            <div class="grid grid-cols-2 gap-6">
                                <div
                                    v-for="(stat, index) in stats"
                                    :key="index"
                                    :class="[
                                        'rounded-xl p-6 text-center',
                                        stat.color === 'blue'
                                            ? 'bg-blue-50 dark:bg-blue-900/20'
                                            : stat.color === 'green'
                                            ? 'bg-green-50 dark:bg-green-900/20'
                                            : stat.color === 'purple'
                                            ? 'bg-purple-50 dark:bg-purple-900/20'
                                            : 'bg-orange-50 dark:bg-orange-900/20',
                                    ]"
                                >
                                    <div
                                        :class="[
                                            'text-3xl font-bold mb-2',
                                            stat.color === 'blue'
                                                ? 'text-blue-600 dark:text-blue-400'
                                                : stat.color === 'green'
                                                ? 'text-green-600 dark:text-green-400'
                                                : stat.color === 'purple'
                                                ? 'text-purple-600 dark:text-purple-400'
                                                : 'text-orange-600 dark:text-orange-400',
                                        ]"
                                    >
                                        {{ stat.value }}
                                    </div>
                                    <div
                                        class="text-gray-700 dark:text-gray-300"
                                    >
                                        {{ stat.label }}
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>
