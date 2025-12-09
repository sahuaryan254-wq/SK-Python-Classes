<template>
    <div class="home-page">
        <Header />
        
        <!-- Hero Section -->
        <section id="home" class="hero-section bg-gradient-to-r from-blue-600 to-indigo-700 text-white py-20">
            <div class="container mx-auto px-4 text-center">
                <h1 class="text-5xl font-bold mb-4">SK Python Classes</h1>
                <p class="text-xl mb-8">Master Python Programming with Expert Guidance</p>
                <div class="flex gap-4 justify-center">
                    <button class="bg-white text-blue-600 px-8 py-3 rounded-lg font-semibold hover:bg-gray-100 transition">
                        Enroll Now
                    </button>
                    <button class="border-2 border-white text-white px-8 py-3 rounded-lg font-semibold hover:bg-white hover:text-blue-600 transition">
                        Learn More
                    </button>
                </div>
            </div>
        </section>

        <!-- About Section -->
        <section id="about" class="about-section py-16 bg-gray-50">
            <div class="container mx-auto px-4">
                <div class="text-center mb-12">
                    <h2 class="text-4xl font-bold text-gray-800 mb-4">About SK Python Classes</h2>
                    <p class="text-gray-600 max-w-2xl mx-auto">
                        We are a premier coaching institute dedicated to teaching Python programming 
                        from basics to advanced levels. Our expert instructors provide hands-on training 
                        and real-world project experience.
                    </p>
                </div>
                <div class="grid md:grid-cols-3 gap-8 mt-12">
                    <div class="bg-white p-6 rounded-lg shadow-md text-center">
                        <div class="text-4xl mb-4">📚</div>
                        <h3 class="text-xl font-semibold mb-2">Expert Instructors</h3>
                        <p class="text-gray-600">Learn from industry professionals with years of experience</p>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-md text-center">
                        <div class="text-4xl mb-4">💻</div>
                        <h3 class="text-xl font-semibold mb-2">Hands-on Projects</h3>
                        <p class="text-gray-600">Build real-world applications and enhance your portfolio</p>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-md text-center">
                        <div class="text-4xl mb-4">🎯</div>
                        <h3 class="text-xl font-semibold mb-2">Career Support</h3>
                        <p class="text-gray-600">Get placement assistance and career guidance</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Courses Section -->
        <section id="courses" class="courses-section py-16">
            <div class="container mx-auto px-4">
                <h2 class="text-4xl font-bold text-center mb-12 text-gray-800">Our Courses</h2>
                <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                    <div 
                        v-for="course in courses" 
                        :key="course.id"
                        class="bg-white border border-gray-200 rounded-lg p-6 hover:shadow-lg transition"
                    >
                        <h3 class="text-2xl font-semibold mb-3 text-blue-600">{{ course.name }}</h3>
                        <p class="text-gray-600 mb-4">{{ course.description }}</p>
                        <div class="flex justify-between items-center">
                            <span class="text-lg font-bold text-gray-800">₹{{ course.price }}</span>
                            <button class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700 transition">
                                Enroll
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Why Choose Us Section -->
        <section id="features" class="why-choose-section py-16 bg-blue-50">
            <div class="container mx-auto px-4">
                <h2 class="text-4xl font-bold text-center mb-12 text-gray-800">Why Choose SK Python Classes?</h2>
                <div class="grid md:grid-cols-2 gap-8">
                    <div 
                        v-for="(feature, index) in features" 
                        :key="index"
                        class="bg-white p-6 rounded-lg shadow-md"
                    >
                        <div class="flex items-start">
                            <div class="text-3xl mr-4">{{ feature.icon }}</div>
                            <div>
                                <h3 class="text-xl font-semibold mb-2">{{ feature.title }}</h3>
                                <p class="text-gray-600">{{ feature.description }}</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <Footer />
    </div>
</template>

<script>
import { ref } from 'vue';
import Header from './Header.vue';
import Footer from './Footer.vue';

export default {
    name: 'Home',
    components: {
        Header,
        Footer
    },
    setup() {
        const courses = ref([
            {
                id: 1,
                name: 'Python Basics',
                description: 'Learn Python fundamentals, syntax, and basic programming concepts.',
                price: 5000
            },
            {
                id: 2,
                name: 'Python Advanced',
                description: 'Master advanced Python concepts including OOP, decorators, and generators.',
                price: 8000
            },
            {
                id: 3,
                name: 'Django Web Development',
                description: 'Build web applications using Django framework.',
                price: 10000
            },
            {
                id: 4,
                name: 'Data Science with Python',
                description: 'Learn data analysis, visualization, and machine learning with Python.',
                price: 12000
            },
            {
                id: 5,
                name: 'Python for Automation',
                description: 'Automate tasks and workflows using Python scripts.',
                price: 7000
            },
            {
                id: 6,
                name: 'Full Stack Python',
                description: 'Complete full-stack development course with Python and modern frameworks.',
                price: 15000
            }
        ]);

        const features = ref([
            {
                icon: '✅',
                title: 'Expert Faculty',
                description: 'Learn from industry experts with years of real-world experience in Python development.'
            },
            {
                icon: '📖',
                title: 'Comprehensive Curriculum',
                description: 'Well-structured courses covering everything from basics to advanced topics.'
            },
            {
                icon: '🖥️',
                title: 'Live Projects',
                description: 'Work on real-world projects to build a strong portfolio and gain practical experience.'
            },
            {
                icon: '👥',
                title: 'Small Batch Size',
                description: 'Personalized attention with small class sizes for better learning experience.'
            },
            {
                icon: '📜',
                title: 'Certification',
                description: 'Get industry-recognized certificates upon course completion.'
            },
            {
                icon: '💼',
                title: 'Placement Assistance',
                description: 'We help you land your dream job with resume building and interview preparation.'
            }
        ]);

        return {
            courses,
            features
        };
    }
};
</script>

<style scoped>
.home-page {
    min-height: 100vh;
}

.hero-section {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.container {
    max-width: 1200px;
    margin: 0 auto;
}
</style>

