<script setup>
import { Head } from "@inertiajs/vue3";
import { ref, computed } from "vue";
import {
    Navigation,
    Hero,
    Features,
    About,
    CTA,
    Contact,
    Footer,
} from "@/Components/Home";

const props = defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    appName: {
        type: String,
        default: "Nexus",
    },
});

const scrollToSection = (sectionId) => {
    const element = document.getElementById(sectionId);
    if (element) {
        element.scrollIntoView({ behavior: "smooth" });
    }
};
</script>

<template>
    <Head title="Welcome" />

    <div class="min-h-screen bg-white dark:bg-gray-900">
        <!-- Navigation -->
        <Navigation
            :can-login="canLogin"
            :can-register="canRegister"
            :app-name="appName"
            @scroll-to-section="scrollToSection"
        />

        <!-- Hero Section -->
        <Hero
            :can-register="canRegister"
            @scroll-to-features="scrollToSection('features')"
        />

        <!-- Features Section -->
        <Features />

        <!-- About Section -->
        <About />

        <!-- CTA Section -->
        <CTA
            :can-register="canRegister"
            @contact-click="scrollToSection('contact')"
        />

        <!-- Contact Section -->
        <Contact />

        <!-- Footer -->
        <Footer :app-name="appName" />
    </div>
</template>
