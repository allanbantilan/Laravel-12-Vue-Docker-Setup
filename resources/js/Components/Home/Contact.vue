<script setup>
const contactMethods = [
    {
        title: "Email Us",
        details: ["support@example.com", "sales@example.com"],
        icon: "M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z",
        color: "blue",
    },
    {
        title: "Visit Us",
        details: ["123 Tech Street", "San Francisco, CA 94107"],
        icon: "M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z M15 11a3 3 0 11-6 0 3 3 0 016 0z",
        color: "green",
    },
    {
        title: "Call Us",
        details: ["+1 (555) 123-4567", "Mon-Fri 9am-6pm PST"],
        icon: "M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z",
        color: "purple",
    },
];
</script>

<template>
    <section id="contact" class="py-20 px-4 sm:px-6 lg:px-8">
        <div class="max-w-7xl mx-auto">
            <div class="text-center mb-16">
                <h2
                    class="text-4xl md:text-5xl font-bold text-gray-900 dark:text-white mb-4"
                >
                    Get in Touch
                </h2>
                <p
                    class="text-xl text-gray-600 dark:text-gray-300 max-w-3xl mx-auto"
                >
                    Have questions? We're here to help. Reach out to our team
                    and we'll get back to you as soon as possible.
                </p>
            </div>

            <div class="grid lg:grid-cols-3 gap-8">
                <div
                    v-for="(method, index) in contactMethods"
                    :key="index"
                    class="bg-white dark:bg-gray-800 rounded-2xl p-8 shadow-lg"
                >
                    <div
                        :class="[
                            'w-12 h-12 rounded-xl flex items-center justify-center mb-6',
                            method.color === 'blue'
                                ? 'bg-blue-100 dark:bg-blue-900/30'
                                : method.color === 'green'
                                ? 'bg-green-100 dark:bg-green-900/30'
                                : 'bg-purple-100 dark:bg-purple-900/30',
                        ]"
                    >
                        <svg
                            :class="[
                                'w-6 h-6',
                                method.color === 'blue'
                                    ? 'text-blue-600 dark:text-blue-400'
                                    : method.color === 'green'
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
                                :d="method.icon"
                            />
                        </svg>
                    </div>
                    <h3
                        class="text-xl font-bold text-gray-900 dark:text-white mb-2"
                    >
                        {{ method.title }}
                    </h3>
                    <p
                        v-for="(detail, detailIndex) in method.details"
                        :key="detailIndex"
                        class="text-gray-600 dark:text-gray-300"
                    >
                        {{ detail }}
                    </p>
                </div>
            </div>
        </div>
    </section>
</template>
