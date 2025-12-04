<script setup>
import { computed } from "vue";

defineProps({
    title: String,
});

const classes = computed(
    () =>
        "min-h-screen flex flex-col sm:justify-center items-center pt-6 sm:pt-0 bg-gradient-to-br from-gray-50 to-gray-100 dark:from-gray-900 dark:to-gray-800 px-4"
);
</script>

<template>
    <div :class="classes">
        <div
            class="w-full sm:max-w-md mt-6 px-6 py-8 bg-white dark:bg-gray-800 shadow-xl overflow-hidden sm:rounded-2xl border border-gray-200 dark:border-gray-700"
        >
            <slot />
        </div>
    </div>
</template>
