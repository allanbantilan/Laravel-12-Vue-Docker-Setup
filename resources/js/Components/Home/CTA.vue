<script setup>
import { Link } from "@inertiajs/vue3";

const props = defineProps({
    canRegister: {
        type: Boolean,
    },
});

const emit = defineEmits(["contact-click"]);
</script>

<template>
    <section
        class="py-20 px-4 sm:px-6 lg:px-8 bg-gradient-to-r from-blue-600 to-indigo-700"
    >
        <div class="max-w-4xl mx-auto text-center">
            <h2 class="text-4xl md:text-5xl font-bold text-white mb-6">
                Ready to Get Started?
            </h2>
            <p class="text-xl text-blue-100 mb-10 max-w-2xl mx-auto">
                Join thousands of satisfied customers building amazing digital
                experiences with our platform.
            </p>
            <div class="flex flex-col sm:flex-row gap-4 justify-center">
                <Link
                    v-if="canRegister"
                    :href="route('register')"
                    class="px-8 py-4 bg-white text-blue-600 hover:bg-blue-50 rounded-xl font-semibold text-lg shadow-lg hover:shadow-xl transform hover:-translate-y-1 transition-all duration-300"
                >
                    Start Free Trial
                </Link>
                <button
                    @click="$emit('contact-click')"
                    class="px-8 py-4 bg-transparent border-2 border-white text-white hover:bg-white/10 rounded-xl font-semibold text-lg transition-all duration-300"
                >
                    Contact Sales
                </button>
            </div>
        </div>
    </section>
</template>