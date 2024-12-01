<template>
    <div class="min-h-screen bg-gray-50 py-12 px-4 sm:px-6 lg:px-8">
        <!-- Header -->
        <div class="text-center max-w-3xl mx-auto mb-16">
            <h1 class="text-4xl font-bold text-gray-900 mb-4">Choose your plan</h1>
            <p class="text-lg text-gray-600">Select the perfect plan for your needs</p>
        </div>

        <!-- Pricing Cards -->
        <div class="max-w-7xl mx-auto grid gap-8 lg:grid-cols-3 mb-16">
            <!-- Professional Plan -->
            <div class="bg-white rounded-lg shadow-lg overflow-hidden">
                <div class="px-6 py-8">
                    <h3 class="text-xl font-semibold text-gray-900 mb-2">Professional</h3>
                    <div class="mt-4 flex items-baseline">
                        <span class="text-5xl font-extrabold text-gray-900">$509</span>
                        <span class="ml-2 text-gray-500">/month</span>
                    </div>
                    <ul class="mt-6 space-y-4">
                        <li class="flex items-start">
                            <CheckIcon class="h-5 w-5 text-green-500 mr-2" />
                            <span class="text-gray-600">24/7 Support</span>
                        </li>
                        <li class="flex items-start">
                            <CheckIcon class="h-5 w-5 text-green-500 mr-2" />
                            <span class="text-gray-600">Analytics Dashboard</span>
                        </li>
                        <li class="flex items-start">
                            <CheckIcon class="h-5 w-5 text-green-500 mr-2" />
                            <span class="text-gray-600">API Access</span>
                        </li>
                    </ul>
                    <button
                        class="mt-8 w-full bg-blue-600 text-white py-3 px-4 rounded-md hover:bg-blue-700 transition duration-150">
                        Get started
                    </button>
                </div>
            </div>

            <!-- Business Plan -->
            <div class="bg-white rounded-lg shadow-lg overflow-hidden border-2 border-blue-500">
                <div class="px-6 py-8">
                    <h3 class="text-xl font-semibold text-gray-900 mb-2">Business</h3>
                    <div class="mt-4 flex items-baseline">
                        <span class="text-5xl font-extrabold text-gray-900">$849</span>
                        <span class="ml-2 text-gray-500">/month</span>
                    </div>
                    <ul class="mt-6 space-y-4">
                        <li class="flex items-start">
                            <CheckIcon class="h-5 w-5 text-green-500 mr-2" />
                            <span class="text-gray-600">Everything from Professional</span>
                        </li>
                        <li class="flex items-start">
                            <CheckIcon class="h-5 w-5 text-green-500 mr-2" />
                            <span class="text-gray-600">Advanced Analytics</span>
                        </li>
                        <li class="flex items-start">
                            <CheckIcon class="h-5 w-5 text-green-500 mr-2" />
                            <span class="text-gray-600">Custom Integrations</span>
                        </li>
                    </ul>
                    <button
                        class="mt-8 w-full bg-blue-600 text-white py-3 px-4 rounded-md hover:bg-blue-700 transition duration-150">
                        Get started
                    </button>
                </div>
            </div>

            <!-- Enterprise Plan -->
            <div class="bg-white rounded-lg shadow-lg overflow-hidden">
                <div class="px-6 py-8">
                    <h3 class="text-xl font-semibold text-gray-900 mb-2">Enterprise</h3>
                    <div class="mt-4 flex items-baseline">
                        <span class="text-5xl font-extrabold text-gray-900">$1,699</span>
                        <span class="ml-2 text-gray-500">/month</span>
                    </div>
                    <ul class="mt-6 space-y-4">
                        <li class="flex items-start">
                            <CheckIcon class="h-5 w-5 text-green-500 mr-2" />
                            <span class="text-gray-600">Everything from Business plus...</span>
                        </li>
                        <li class="flex items-start">
                            <CheckIcon class="h-5 w-5 text-green-500 mr-2" />
                            <span class="text-gray-600">Dedicated Support</span>
                        </li>
                        <li class="flex items-start">
                            <CheckIcon class="h-5 w-5 text-green-500 mr-2" />
                            <span class="text-gray-600">Custom Solutions</span>
                        </li>
                    </ul>
                    <button
                        class="mt-8 w-full bg-blue-600 text-white py-3 px-4 rounded-md hover:bg-blue-700 transition duration-150">
                        Get started
                    </button>
                </div>
            </div>
        </div>

        <!-- Feature Comparison Table -->
        <div class="max-w-7xl mx-auto">
            <table class="w-full">
                <thead>
                    <tr class="border-t border-gray-200">
                        <th class="py-5 px-4 text-left text-sm font-medium text-gray-500">Features</th>
                        <th class="py-5 px-4 text-center text-sm font-medium text-gray-500">Professional</th>
                        <th class="py-5 px-4 text-center text-sm font-medium text-gray-500">Business</th>
                        <th class="py-5 px-4 text-center text-sm font-medium text-gray-500">Enterprise</th>
                    </tr>
                </thead>
                <tbody class="divide-y divide-gray-200">
                    <tr v-for="feature in features" :key="feature.name">
                        <td class="py-4 px-4 text-sm text-gray-900">{{ feature.name }}</td>
                        <td class="py-4 px-4 text-center">
                            <CheckIcon v-if="feature.professional" class="h-5 w-5 text-green-500 mx-auto" />
                        </td>
                        <td class="py-4 px-4 text-center">
                            <CheckIcon v-if="feature.business" class="h-5 w-5 text-green-500 mx-auto" />
                        </td>
                        <td class="py-4 px-4 text-center">
                            <CheckIcon v-if="feature.enterprise" class="h-5 w-5 text-green-500 mx-auto" />
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
import { CheckIcon } from '@heroicons/vue/20/solid';

export default {
    components: {
        CheckIcon,
    },
    data() {
        return {
            features: [
                {
                    name: 'Basic features',
                    professional: true,
                    business: true,
                    enterprise: true,
                },
                {
                    name: 'Advanced analytics',
                    professional: false,
                    business: true,
                    enterprise: true,
                },
                {
                    name: 'Custom integrations',
                    professional: false,
                    business: true,
                    enterprise: true,
                },
                {
                    name: 'API access',
                    professional: true,
                    business: true,
                    enterprise: true,
                },
                {
                    name: 'Dedicated support',
                    professional: false,
                    business: false,
                    enterprise: true,
                },
                {
                    name: 'Custom solutions',
                    professional: false,
                    business: false,
                    enterprise: true,
                },
            ],
        };
    },
};
</script>
