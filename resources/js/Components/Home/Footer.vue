<script setup>
const props = defineProps({
    appName: {
        type: String,
        default: "Nexus",
    },
});

const currentYear = new Date().getFullYear();

const links = {
    product: [
        { label: "Features", href: "#" },
        { label: "Pricing", href: "#" },
        { label: "API", href: "#" },
        { label: "Documentation", href: "#" },
    ],
    company: [
        { label: "About", href: "#" },
        { label: "Blog", href: "#" },
        { label: "Careers", href: "#" },
        { label: "Press", href: "#" },
    ],
    legal: [
        { label: "Privacy Policy", href: "#" },
        { label: "Terms of Service", href: "#" },
        { label: "Cookie Policy", href: "#" },
        { label: "GDPR", href: "#" },
    ],
};
</script>

<template>
    <footer class="bg-gray-900 text-white py-12 px-4 sm:px-6 lg:px-8">
        <div class="max-w-7xl mx-auto">
            <div class="grid md:grid-cols-4 gap-8">
                <div>
                    <div class="flex items-center space-x-2 mb-6">
                        <div
                            class="w-10 h-10 bg-gradient-to-br from-blue-500 to-indigo-500 rounded-xl flex items-center justify-center"
                        >
                            <svg
                                class="w-6 h-6 text-white"
                                fill="none"
                                stroke="currentColor"
                                viewBox="0 0 24 24"
                            >
                                <path
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                    stroke-width="2"
                                    d="M13 10V3L4 14h7v7l9-11h-7z"
                                />
                            </svg>
                        </div>
                        <span class="text-xl font-bold">
                            {{ appName }}
                        </span>
                    </div>
                    <p class="text-gray-400">
                        Building the future of digital experiences, one platform
                        at a time.
                    </p>
                </div>
                <div>
                    <h3 class="text-lg font-semibold mb-4">Product</h3>
                    <ul class="space-y-2 text-gray-400">
                        <li v-for="(link, index) in links.product" :key="index">
                            <a
                                :href="link.href"
                                class="hover:text-white transition-colors"
                            >
                                {{ link.label }}
                            </a>
                        </li>
                    </ul>
                </div>
                <div>
                    <h3 class="text-lg font-semibold mb-4">Company</h3>
                    <ul class="space-y-2 text-gray-400">
                        <li v-for="(link, index) in links.company" :key="index">
                            <a
                                :href="link.href"
                                class="hover:text-white transition-colors"
                            >
                                {{ link.label }}
                            </a>
                        </li>
                    </ul>
                </div>
                <div>
                    <h3 class="text-lg font-semibold mb-4">Legal</h3>
                    <ul class="space-y-2 text-gray-400">
                        <li v-for="(link, index) in links.legal" :key="index">
                            <a
                                :href="link.href"
                                class="hover:text-white transition-colors"
                            >
                                {{ link.label }}
                            </a>
                        </li>
                    </ul>
                </div>
            </div>
            <div
                class="border-t border-gray-800 mt-8 pt-8 text-center text-gray-400"
            >
                <p>
                    &copy; {{ currentYear }} {{ appName }}. All rights reserved.
                </p>
            </div>
        </div>
    </footer>
</template>
