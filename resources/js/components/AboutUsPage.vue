<template>
    <div class="min-h-screen bg-gradient-to-br from-gray-50 via-blue-50/20 to-purple-50/20">
        <Header />
        
        <!-- About Us Section -->
        <section class="py-8 sm:py-12 lg:py-16">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8 max-w-4xl">
                <!-- Page Header -->
                <div class="text-center mb-8 sm:mb-12">
                    <div class="inline-flex items-center justify-center w-16 h-16 sm:w-20 sm:h-20 bg-gradient-to-br from-indigo-500 to-purple-500 rounded-xl sm:rounded-2xl shadow-xl mb-4 sm:mb-6">
                        <svg class="w-8 h-8 sm:w-10 sm:h-10 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 10v-5a1 1 0 011-1h2a1 1 0 011 1v5m-4 0h4" />
                        </svg>
                    </div>
                    <h1 class="text-2xl sm:text-3xl lg:text-4xl xl:text-5xl font-bold bg-gradient-to-r from-indigo-600 via-purple-600 to-indigo-600 bg-clip-text text-transparent mb-3 sm:mb-4 px-2">
                        About Us
                    </h1>
                    <p class="text-sm sm:text-base lg:text-lg text-gray-600 max-w-2xl mx-auto px-2">
                        Learn more about SK Python Classes and our mission to empower students with Python programming skills.
                    </p>
                </div>

                <!-- About Content -->
                <div class="bg-white rounded-xl sm:rounded-2xl shadow-xl border border-gray-100 overflow-hidden">
                    <div class="p-6 sm:p-8 lg:p-10">
                        <!-- Main Description -->
                        <div class="prose prose-sm sm:prose-base lg:prose-lg max-w-none mb-8">
                            <p class="text-gray-700 leading-relaxed mb-4">
                                Welcome to <strong class="text-indigo-600">SK Python Classes</strong>, a premier coaching institute dedicated to teaching Python programming from basics to advanced levels. We are committed to providing high-quality education and hands-on training to help you build a successful career in technology.
                            </p>
                            <p class="text-gray-700 leading-relaxed mb-4">
                                Our expert instructors bring years of real-world experience in Python development, ensuring that you learn not just the theory, but also practical skills that are in demand in today's job market.
                            </p>
                        </div>

                        <!-- Features Grid -->
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-6 mb-8">
                            <div class="flex items-start space-x-4 p-4 bg-gradient-to-br from-blue-50 to-indigo-50 rounded-xl">
                                <div class="flex-shrink-0 w-12 h-12 bg-gradient-to-br from-blue-500 to-indigo-500 rounded-lg flex items-center justify-center">
                                    <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253" />
                                    </svg>
                                </div>
                                <div>
                                    <h3 class="text-lg font-bold text-gray-900 mb-1">Expert Instructors</h3>
                                    <p class="text-sm text-gray-600">Learn from industry professionals with years of experience</p>
                                </div>
                            </div>

                            <div class="flex items-start space-x-4 p-4 bg-gradient-to-br from-purple-50 to-pink-50 rounded-xl">
                                <div class="flex-shrink-0 w-12 h-12 bg-gradient-to-br from-purple-500 to-pink-500 rounded-lg flex items-center justify-center">
                                    <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z" />
                                    </svg>
                                </div>
                                <div>
                                    <h3 class="text-lg font-bold text-gray-900 mb-1">Hands-on Projects</h3>
                                    <p class="text-sm text-gray-600">Build real-world applications and enhance your portfolio</p>
                                </div>
                            </div>

                            <div class="flex items-start space-x-4 p-4 bg-gradient-to-br from-green-50 to-emerald-50 rounded-xl">
                                <div class="flex-shrink-0 w-12 h-12 bg-gradient-to-br from-green-500 to-emerald-500 rounded-lg flex items-center justify-center">
                                    <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
                                    </svg>
                                </div>
                                <div>
                                    <h3 class="text-lg font-bold text-gray-900 mb-1">Certification</h3>
                                    <p class="text-sm text-gray-600">Get industry-recognized certificates upon completion</p>
                                </div>
                            </div>

                            <div class="flex items-start space-x-4 p-4 bg-gradient-to-br from-orange-50 to-red-50 rounded-xl">
                                <div class="flex-shrink-0 w-12 h-12 bg-gradient-to-br from-orange-500 to-red-500 rounded-lg flex items-center justify-center">
                                    <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 13.255A23.931 23.931 0 0112 15c-3.183 0-6.22-.62-9-1.745M16 6V4a2 2 0 00-2-2h-4a2 2 0 00-2 2v2m4 6h.01M5 20h14a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                                    </svg>
                                </div>
                                <div>
                                    <h3 class="text-lg font-bold text-gray-900 mb-1">Career Support</h3>
                                    <p class="text-sm text-gray-600">Get placement assistance and career guidance</p>
                                </div>
                            </div>
                        </div>

                        <!-- Mission Section -->
                        <div class="bg-gradient-to-r from-indigo-50 via-purple-50 to-indigo-50 rounded-xl p-6 sm:p-8 mb-8">
                            <h2 class="text-2xl sm:text-3xl font-bold text-gray-900 mb-4">Our Mission</h2>
                            <p class="text-gray-700 leading-relaxed">
                                Our mission is to make quality Python programming education accessible to everyone. We believe that with the right guidance and resources, anyone can learn to code and build amazing applications. We are committed to providing a supportive learning environment where students can grow, experiment, and achieve their career goals.
                            </p>
                        </div>

                        <!-- Why Choose Us -->
                        <div>
                            <h2 class="text-2xl sm:text-3xl font-bold text-gray-900 mb-6">Why Choose SK Python Classes?</h2>
                            <ul class="space-y-4">
                                <li class="flex items-start space-x-3">
                                    <svg class="w-6 h-6 text-green-500 flex-shrink-0 mt-0.5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                                    </svg>
                                    <span class="text-gray-700">Small batch sizes for personalized attention</span>
                                </li>
                                <li class="flex items-start space-x-3">
                                    <svg class="w-6 h-6 text-green-500 flex-shrink-0 mt-0.5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                                    </svg>
                                    <span class="text-gray-700">Comprehensive curriculum covering all aspects of Python</span>
                                </li>
                                <li class="flex items-start space-x-3">
                                    <svg class="w-6 h-6 text-green-500 flex-shrink-0 mt-0.5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                                    </svg>
                                    <span class="text-gray-700">Live classes and interactive sessions</span>
                                </li>
                                <li class="flex items-start space-x-3">
                                    <svg class="w-6 h-6 text-green-500 flex-shrink-0 mt-0.5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                                    </svg>
                                    <span class="text-gray-700">Flexible learning schedules</span>
                                </li>
                                <li class="flex items-start space-x-3">
                                    <svg class="w-6 h-6 text-green-500 flex-shrink-0 mt-0.5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                                    </svg>
                                    <span class="text-gray-700">Lifetime access to course materials</span>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <Footer />
    </div>
</template>

<script>
import Header from './Header.vue';
import Footer from './Footer.vue';

export default {
    name: 'AboutUsPage',
    components: {
        Header,
        Footer
    }
};
</script>

<style scoped>
.container {
    max-width: 1280px;
    margin: 0 auto;
}
</style>

