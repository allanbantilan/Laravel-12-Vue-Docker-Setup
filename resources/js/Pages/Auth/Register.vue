<script setup>
import { Head, Link, useForm, usePage } from "@inertiajs/vue3";
import { computed } from "vue";
import { Navigation, Footer } from "@/Components/Home";
import Checkbox from "@/Components/Checkbox.vue";
import InputError from "@/Components/InputError.vue";
import InputLabel from "@/Components/InputLabel.vue";
import TextInput from "@/Components/TextInput.vue";

const page = usePage();
const appName = computed(() => page.props.appName || "Laravel");

const form = useForm({
    name: "",
    email: "",
    password: "",
    password_confirmation: "",
    terms: false,
});

const submit = () => {
    form.post(route("register"), {
        onFinish: () => form.reset("password", "password_confirmation"),
    });
};
</script>

<template>
    <Head title="Register" />

    <div class="min-h-screen bg-white dark:bg-gray-900">
        <!-- Navigation -->
        <Navigation
            :can-login="true"
            :can-register="false"
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
                            CREATE ACCOUNT
                        </h1>
                        <p class="text-gray-600 dark:text-gray-300">
                            Join {{ appName }} and get started
                        </p>
                    </div>

                    <!-- Form -->
                    <div
                        class="bg-white dark:bg-gray-800 rounded-2xl shadow-xl p-8 border border-gray-200 dark:border-gray-700"
                    >
                        <form @submit.prevent="submit" class="space-y-6">
                            <!-- Name Input -->
                            <div>
                                <InputLabel
                                    for="name"
                                    value="Full Name"
                                    class="text-gray-700 dark:text-gray-300 font-medium mb-2"
                                />
                                <TextInput
                                    id="name"
                                    v-model="form.name"
                                    type="text"
                                    class="mt-1 block w-full rounded-lg border-gray-300 dark:border-gray-600 dark:bg-gray-700 dark:text-white focus:border-indigo-500 focus:ring-indigo-500 dark:focus:border-indigo-400 dark:focus:ring-indigo-400 py-3 px-4"
                                    required
                                    autofocus
                                    autocomplete="name"
                                    placeholder="Enter your full name"
                                />
                                <InputError
                                    class="mt-2"
                                    :message="form.errors.name"
                                />
                            </div>

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
                                <InputLabel
                                    for="password"
                                    value="Password"
                                    class="text-gray-700 dark:text-gray-300 font-medium mb-2"
                                />
                                <TextInput
                                    id="password"
                                    v-model="form.password"
                                    type="password"
                                    class="mt-1 block w-full rounded-lg border-gray-300 dark:border-gray-600 dark:bg-gray-700 dark:text-white focus:border-indigo-500 focus:ring-indigo-500 dark:focus:border-indigo-400 dark:focus:ring-indigo-400 py-3 px-4"
                                    required
                                    autocomplete="new-password"
                                    placeholder="Create a strong password"
                                />
                                <div
                                    class="mt-2 text-xs text-gray-500 dark:text-gray-400"
                                >
                                    Use at least 8 characters with a mix of
                                    letters, numbers & symbols
                                </div>
                                <InputError
                                    class="mt-2"
                                    :message="form.errors.password"
                                />
                            </div>

                            <!-- Confirm Password Input -->
                            <div>
                                <InputLabel
                                    for="password_confirmation"
                                    value="Confirm Password"
                                    class="text-gray-700 dark:text-gray-300 font-medium mb-2"
                                />
                                <TextInput
                                    id="password_confirmation"
                                    v-model="form.password_confirmation"
                                    type="password"
                                    class="mt-1 block w-full rounded-lg border-gray-300 dark:border-gray-600 dark:bg-gray-700 dark:text-white focus:border-indigo-500 focus:ring-indigo-500 dark:focus:border-indigo-400 dark:focus:ring-indigo-400 py-3 px-4"
                                    required
                                    autocomplete="new-password"
                                    placeholder="Confirm your password"
                                />
                                <InputError
                                    class="mt-2"
                                    :message="form.errors.password_confirmation"
                                />
                            </div>

                            <!-- Terms Agreement -->
                            <div
                                v-if="
                                    $page.props.jetstream
                                        .hasTermsAndPrivacyPolicyFeature
                                "
                                class="mt-4"
                            >
                                <label class="flex items-start">
                                    <Checkbox
                                        id="terms"
                                        v-model:checked="form.terms"
                                        name="terms"
                                        required
                                        class="mt-1 text-indigo-600 dark:text-indigo-400 focus:ring-indigo-500 dark:focus:ring-indigo-400 border-gray-300 dark:border-gray-600"
                                    />
                                    <span
                                        class="ms-3 text-sm text-gray-600 dark:text-gray-300"
                                    >
                                        I agree to the
                                        <a
                                            target="_blank"
                                            :href="route('terms.show')"
                                            class="text-indigo-600 dark:text-indigo-400 hover:text-indigo-500 dark:hover:text-indigo-300 font-medium"
                                            >Terms of Service</a
                                        >
                                        and
                                        <a
                                            target="_blank"
                                            :href="route('policy.show')"
                                            class="text-indigo-600 dark:text-indigo-400 hover:text-indigo-500 dark:hover:text-indigo-300 font-medium"
                                            >Privacy Policy</a
                                        >
                                    </span>
                                </label>
                                <InputError
                                    class="mt-2"
                                    :message="form.errors.terms"
                                />
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
                                        Creating account...
                                    </span>
                                    <span v-else class="text-lg"
                                        >Create Account</span
                                    >
                                </button>
                            </div>

                            <!-- Login Link -->
                            <div
                                class="mt-6 pt-6 border-t border-gray-200 dark:border-gray-700 text-center"
                            >
                                <p class="text-gray-600 dark:text-gray-300">
                                    Already have an account?
                                    <Link
                                        :href="route('login')"
                                        class="text-indigo-600 dark:text-indigo-400 hover:text-indigo-500 dark:hover:text-indigo-300 font-semibold ml-1"
                                    >
                                        Sign in here
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
