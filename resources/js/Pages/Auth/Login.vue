<script setup>
import { Head, Link, useForm, usePage } from "@inertiajs/vue3";
import { computed } from "vue";
import { Navigation, Footer } from "@/Components/Home";
import Checkbox from "@/Components/Checkbox.vue";
import InputError from "@/Components/InputError.vue";
import InputLabel from "@/Components/InputLabel.vue";
import TextInput from "@/Components/TextInput.vue";

const props = defineProps({
    canResetPassword: Boolean,
    status: String,
});

const page = usePage();
const appName = computed(() => page.props.appName || "Laravel");

const form = useForm({
    email: "",
    password: "",
    remember: false,
});

const submit = () => {
    form.transform((data) => ({
        ...data,
        remember: form.remember ? "on" : "",
    })).post(route("login"), {
        onFinish: () => form.reset("password"),
    });
};

const scrollToSection = (sectionId) => {
    const element = document.getElementById(sectionId);
    if (element) {
        element.scrollIntoView({ behavior: "smooth" });
    }
};
</script>

<template>
    <Head title="Sign In" />

    <div class="min-h-screen bg-white dark:bg-gray-900">
        <!-- Navigation -->
        <Navigation
            :can-login="false"
            :can-register="true"
            :hide-main-links="true"
            @scroll-to-section="scrollToSection"
        />

        <!-- Main Content -->
        <main class="pt-20 pb-12">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="max-w-md mx-auto">
                    <!-- Logo and Title -->
                    <div class="text-center mb-8">
                        <div class="flex justify-center mb-6">
                            <div
                                class="w-20 h-20 bg-gradient-to-br from-indigo-500 to-indigo-700 rounded-2xl flex items-center justify-center shadow-lg"
                            >
                                <div class="text-white text-2xl font-bold">
                                    {{ appName.charAt(0) }}
                                </div>
                            </div>
                        </div>

                        <h1
                            class="text-3xl font-bold text-gray-900 dark:text-white mb-2"
                        >
                            SIGN IN
                        </h1>
                        <p class="text-gray-600 dark:text-gray-300">
                            Welcome back to {{ appName }}! Please enter your
                            credentials
                        </p>
                    </div>

                    <!-- Status Message -->
                    <div
                        v-if="status"
                        class="mb-6 p-4 bg-green-50 dark:bg-green-900/30 border border-green-200 dark:border-green-800 rounded-lg text-green-700 dark:text-green-400 text-sm text-center"
                    >
                        {{ status }}
                    </div>

                    <!-- Form -->
                    <div
                        class="bg-white dark:bg-gray-800 rounded-2xl shadow-xl p-8 border border-gray-200 dark:border-gray-700"
                    >
                        <form @submit.prevent="submit" class="space-y-6">
                            <!-- Email Input -->
                            <div>
                                <InputLabel
                                    for="email"
                                    value="Email Address"
                                    class="text-gray-700 dark:text-gray-300 font-medium mb-2"
                                />
                                <TextInput
                                    id="email"
                                    v-model="form.email"
                                    type="email"
                                    class="mt-1 block w-full rounded-lg border-gray-300 dark:border-gray-600 dark:bg-gray-700 dark:text-white focus:border-indigo-500 focus:ring-indigo-500 dark:focus:border-indigo-400 dark:focus:ring-indigo-400 py-3 px-4"
                                    required
                                    autofocus
                                    autocomplete="username"
                                    placeholder="Enter your email"
                                />
                                <InputError
                                    class="mt-2"
                                    :message="form.errors.email"
                                />
                            </div>

                            <!-- Password Input -->
                            <div>
                                <div
                                    class="flex items-center justify-between mb-2"
                                >
                                    <InputLabel
                                        for="password"
                                        value="Password"
                                        class="text-gray-700 dark:text-gray-300 font-medium"
                                    />
                                    <Link
                                        v-if="canResetPassword"
                                        :href="route('password.request')"
                                        class="text-sm text-indigo-600 dark:text-indigo-400 hover:text-indigo-500 dark:hover:text-indigo-300 font-medium"
                                    >
                                        Forgot password?
                                    </Link>
                                </div>
                                <TextInput
                                    id="password"
                                    v-model="form.password"
                                    type="password"
                                    class="mt-1 block w-full rounded-lg border-gray-300 dark:border-gray-600 dark:bg-gray-700 dark:text-white focus:border-indigo-500 focus:ring-indigo-500 dark:focus:border-indigo-400 dark:focus:ring-indigo-400 py-3 px-4"
                                    required
                                    autocomplete="current-password"
                                    placeholder="Enter your password"
                                />
                                <InputError
                                    class="mt-2"
                                    :message="form.errors.password"
                                />
                            </div>

                            <!-- Remember Me Checkbox -->
                            <div class="flex items-center">
                                <Checkbox
                                    v-model:checked="form.remember"
                                    name="remember"
                                    class="text-indigo-600 dark:text-indigo-400 focus:ring-indigo-500 dark:focus:ring-indigo-400 border-gray-300 dark:border-gray-600"
                                />
                                <span
                                    class="ms-3 text-sm text-gray-600 dark:text-gray-300"
                                    >Keep me signed in</span
                                >
                            </div>

                            <!-- Submit Button -->
                            <div class="mt-8">
                                <button
                                    type="submit"
                                    :disabled="form.processing"
                                    class="w-full py-3 px-4 bg-gradient-to-r from-indigo-600 to-indigo-700 hover:from-indigo-700 hover:to-indigo-800 text-white font-semibold rounded-lg transition-all duration-200 shadow-lg hover:shadow-xl transform hover:-translate-y-0.5 disabled:opacity-50 disabled:cursor-not-allowed disabled:transform-none disabled:hover:shadow-lg"
                                >
                                    <span
                                        v-if="form.processing"
                                        class="flex items-center justify-center"
                                    >
                                        <svg
                                            class="animate-spin -ml-1 mr-3 h-5 w-5 text-white"
                                            xmlns="http://www.w3.org/2000/svg"
                                            fill="none"
                                            viewBox="0 0 24 24"
                                        >
                                            <circle
                                                class="opacity-25"
                                                cx="12"
                                                cy="12"
                                                r="10"
                                                stroke="currentColor"
                                                stroke-width="4"
                                            ></circle>
                                            <path
                                                class="opacity-75"
                                                fill="currentColor"
                                                d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"
                                            ></path>
                                        </svg>
                                        Signing in...
                                    </span>
                                    <span v-else class="text-lg">Sign In</span>
                                </button>
                            </div>

                            <!-- Register Link -->
                            <div
                                class="mt-6 pt-6 border-t border-gray-200 dark:border-gray-700 text-center"
                            >
                                <p class="text-gray-600 dark:text-gray-300">
                                    Don't have an account?
                                    <Link
                                        :href="route('register')"
                                        class="text-indigo-600 dark:text-indigo-400 hover:text-indigo-500 dark:hover:text-indigo-300 font-semibold ml-1"
                                    >
                                        Register now
                                    </Link>
                                </p>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </main>

        <!-- Footer -->
        <Footer :app-name="appName" />
    </div>
</template>
