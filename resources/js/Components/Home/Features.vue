<script setup>
const features = [
    {
        title: "Lightning Fast",
        description:
            "Built for speed with optimized performance and minimal latency. Experience blazing fast load times for your applications.",
        icon: "M13 10V3L4 14h7v7l9-11h-7z",
        color: "blue",
    },
    {
        title: "Enterprise Security",
        description:
            "Military-grade encryption and security protocols to keep your data safe and protected at all times.",
        icon: "M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z",
        color: "green",
    },
    {
        title: "Scalable Infrastructure",
        description:
            "Grow without limits. Our platform scales automatically to handle your traffic and data demands.",
        icon: "M4 5a1 1 0 011-1h14a1 1 0 011 1v2a1 1 0 01-1 1H5a1 1 0 01-1-1V5zM4 13a1 1 0 011-1h6a1 1 0 011 1v6a1 1 0 01-1 1H5a1 1 0 01-1-1v-6zM16 13a1 1 0 011-1h2a1 1 0 011 1v6a1 1 0 01-1 1h-2a1 1 0 01-1-1v-6z",
        color: "purple",
    },
];
</script>

<template>
    <section
        id="features"
        class="py-20 px-4 sm:px-6 lg:px-8 bg-gray-50 dark:bg-gray-800/50"
    >
        <div class="max-w-7xl mx-auto">
            <div class="text-center mb-16">
                <h2
                    class="text-4xl md:text-5xl font-bold text-gray-900 dark:text-white mb-4"
                >
                    Powerful Features
                </h2>
                <p
                    class="text-xl text-gray-600 dark:text-gray-300 max-w-3xl mx-auto"
                >
                    Everything you need to build, launch, and grow your digital
                    presence.
                </p>
            </div>

            <div class="grid md:grid-cols-3 gap-8">
                <div
                    v-for="(feature, index) in features"
                    :key="index"
                    class="bg-white dark:bg-gray-800 rounded-2xl p-8 shadow-lg hover:shadow-xl transition-shadow duration-300"
                >
                    <div
                        :class="[
                            'w-14 h-14 rounded-xl flex items-center justify-center mb-6',
                            feature.color === 'blue'
                                ? 'bg-blue-100 dark:bg-blue-900/30'
                                : feature.color === 'green'
                                ? 'bg-green-100 dark:bg-green-900/30'
                                : 'bg-purple-100 dark:bg-purple-900/30',
                        ]"
                    >
                        <svg
                            :class="[
                                'w-7 h-7',
                                feature.color === 'blue'
                                    ? 'text-blue-600 dark:text-blue-400'
                                    : feature.color === 'green'
                                    ? 'text-green-600 dark:text-green-400'
                                    : 'text-purple-600 dark:text-purple-400',
                            ]"
                            fill="none"
                            stroke="currentColor"
                            viewBox="0 0 24 24"
                        >
                            <path
                                stroke-linecap="round"
                                stroke-linejoin="round"
                                stroke-width="2"
                                :d="feature.icon"
                            />
                        </svg>
                    </div>
                    <h3
                        class="text-2xl font-bold text-gray-900 dark:text-white mb-4"
                    >
                        {{ feature.title }}
                    </h3>
                    <p class="text-gray-600 dark:text-gray-300">
                        {{ feature.description }}
                    </p>
                </div>
            </div>
        </div>
    </section>
</template>
