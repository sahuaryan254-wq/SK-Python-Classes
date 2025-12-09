<template>
    <header class="header-modern sticky top-0 z-50 backdrop-blur-xl bg-white/80 border-b border-gray-200/50 shadow-sm">
        <nav class="container mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16 lg:h-20">
                <!-- Logo -->
                <div class="flex items-center space-x-3 group cursor-pointer">
                    <div class="logo-container">
                        <img 
                            v-if="brandSettings.brand_logo_url" 
                            :src="brandSettings.brand_logo_url" 
                            :alt="brandSettings.brand_name"
                            class="h-10 w-auto lg:h-12 transition-transform duration-300 group-hover:scale-110"
                        >
                    </div>
                    <h1 class="text-xl sm:text-2xl lg:text-3xl font-bold bg-gradient-to-r from-blue-600 via-purple-600 to-blue-600 bg-clip-text text-transparent animate-gradient">
                        {{ brandSettings.brand_name || 'SK Python Classes' }}
                    </h1>
                </div>

                <!-- Navigation Links -->
                <div class="hidden lg:flex items-center space-x-1">
                    <a 
                        href="#home" 
                        class="nav-link relative px-4 py-2 text-sm font-semibold text-gray-700 hover:text-blue-600 transition-all duration-300 rounded-lg hover:bg-blue-50/50 group"
                    >
                        Home
                        <span class="nav-underline"></span>
                    </a>
                    <a 
                        href="#about" 
                        class="nav-link relative px-4 py-2 text-sm font-semibold text-gray-700 hover:text-blue-600 transition-all duration-300 rounded-lg hover:bg-blue-50/50 group"
                    >
                        About
                        <span class="nav-underline"></span>
                    </a>
                    <a 
                        href="#courses" 
                        class="nav-link relative px-4 py-2 text-sm font-semibold text-gray-700 hover:text-blue-600 transition-all duration-300 rounded-lg hover:bg-blue-50/50 group"
                    >
                        Courses
                        <span class="nav-underline"></span>
                    </a>
                    <a 
                        href="#features" 
                        class="nav-link relative px-4 py-2 text-sm font-semibold text-gray-700 hover:text-blue-600 transition-all duration-300 rounded-lg hover:bg-blue-50/50 group"
                    >
                        Features
                        <span class="nav-underline"></span>
                    </a>
                    <a 
                        href="#contact" 
                        class="nav-link relative px-4 py-2 text-sm font-semibold text-gray-700 hover:text-blue-600 transition-all duration-300 rounded-lg hover:bg-blue-50/50 group"
                    >
                        Contact
                        <span class="nav-underline"></span>
                    </a>
                </div>

                <!-- CTA Buttons -->
                <div class="flex items-center space-x-3">
                    <a 
                        href="/login"
                        class="hidden sm:flex items-center justify-center px-5 py-2.5 text-sm font-semibold text-gray-700 hover:text-blue-600 transition-all duration-300 rounded-xl hover:bg-gray-100/80 border border-gray-200/50 hover:border-blue-300/50 hover:shadow-sm"
                    >
                        <svg class="w-4 h-4 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z" />
                        </svg>
                        Login
                    </a>
                    <button 
                        @click="scrollToContact"
                        class="hidden sm:flex items-center justify-center px-6 py-2.5 text-sm font-semibold text-white bg-gradient-to-r from-blue-600 to-purple-600 hover:from-blue-700 hover:to-purple-700 rounded-xl transition-all duration-300 shadow-lg shadow-blue-500/30 hover:shadow-xl hover:shadow-blue-500/40 hover:scale-105 active:scale-95"
                    >
                        <span>Enroll Now</span>
                        <svg class="w-4 h-4 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6" />
                        </svg>
                    </button>
                    
                    <!-- Mobile Menu Button -->
                    <button 
                        @click="toggleMobileMenu"
                        class="lg:hidden p-2.5 text-gray-700 hover:text-blue-600 hover:bg-gray-100/50 rounded-xl transition-all duration-300 focus:outline-none focus:ring-2 focus:ring-blue-500/20 active:scale-95"
                        aria-label="Toggle menu"
                    >
                        <svg 
                            class="w-6 h-6 transition-transform duration-300" 
                            :class="{ 'rotate-90': mobileMenuOpen }"
                            fill="none" 
                            stroke="currentColor" 
                            viewBox="0 0 24 24"
                        >
                            <path 
                                v-if="!mobileMenuOpen" 
                                stroke-linecap="round" 
                                stroke-linejoin="round" 
                                stroke-width="2" 
                                d="M4 6h16M4 12h16M4 18h16" 
                            />
                            <path 
                                v-else 
                                stroke-linecap="round" 
                                stroke-linejoin="round" 
                                stroke-width="2" 
                                d="M6 18L18 6M6 6l12 12" 
                            />
                        </svg>
                    </button>
                </div>
            </div>

            <!-- Mobile Menu -->
            <transition
                enter-active-class="transition-all duration-300 ease-out"
                enter-from-class="opacity-0 -translate-y-4"
                enter-to-class="opacity-100 translate-y-0"
                leave-active-class="transition-all duration-200 ease-in"
                leave-from-class="opacity-100 translate-y-0"
                leave-to-class="opacity-0 -translate-y-4"
            >
                <div v-if="mobileMenuOpen" class="lg:hidden pb-6 pt-2 border-t border-gray-200/50 mt-2">
                    <div class="flex flex-col space-y-2 pt-4">
                        <a 
                            href="#home" 
                            @click="closeMobileMenu" 
                            class="mobile-nav-link px-4 py-3 text-base font-semibold text-gray-700 hover:text-blue-600 hover:bg-blue-50/50 rounded-xl transition-all duration-300"
                        >
                            Home
                        </a>
                        <a 
                            href="#about" 
                            @click="closeMobileMenu" 
                            class="mobile-nav-link px-4 py-3 text-base font-semibold text-gray-700 hover:text-blue-600 hover:bg-blue-50/50 rounded-xl transition-all duration-300"
                        >
                            About
                        </a>
                        <a 
                            href="#courses" 
                            @click="closeMobileMenu" 
                            class="mobile-nav-link px-4 py-3 text-base font-semibold text-gray-700 hover:text-blue-600 hover:bg-blue-50/50 rounded-xl transition-all duration-300"
                        >
                            Courses
                        </a>
                        <a 
                            href="#features" 
                            @click="closeMobileMenu" 
                            class="mobile-nav-link px-4 py-3 text-base font-semibold text-gray-700 hover:text-blue-600 hover:bg-blue-50/50 rounded-xl transition-all duration-300"
                        >
                            Features
                        </a>
                        <a 
                            href="#contact" 
                            @click="closeMobileMenu" 
                            class="mobile-nav-link px-4 py-3 text-base font-semibold text-gray-700 hover:text-blue-600 hover:bg-blue-50/50 rounded-xl transition-all duration-300"
                        >
                            Contact
                        </a>
                        <a 
                            href="/login" 
                            @click="closeMobileMenu" 
                            class="mobile-nav-link px-4 py-3 text-base font-semibold text-gray-700 hover:text-blue-600 hover:bg-blue-50/50 rounded-xl transition-all duration-300 flex items-center"
                        >
                            <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z" />
                            </svg>
                            Login
                        </a>
                        <button 
                            @click="scrollToContact"
                            class="mt-2 px-4 py-3 text-base font-semibold text-white bg-gradient-to-r from-blue-600 to-purple-600 hover:from-blue-700 hover:to-purple-700 rounded-xl transition-all duration-300 shadow-lg shadow-blue-500/30 flex items-center justify-center"
                        >
                            <span>Enroll Now</span>
                            <svg class="w-5 h-5 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6" />
                            </svg>
                        </button>
                    </div>
                </div>
            </transition>
        </nav>
    </header>
</template>

<script>
import { ref, onMounted } from 'vue';
import axios from 'axios';

export default {
    name: 'Header',
    setup() {
        const mobileMenuOpen = ref(false);
        const brandSettings = ref({
            brand_name: 'SK Python Classes',
            brand_logo_url: null
        });

        const fetchBrandSettings = async () => {
            try {
                const response = await axios.get('/api/brand-settings');
                if (response.data.success && response.data.settings) {
                    const settings = response.data.settings;
                    brandSettings.value = {
                        brand_name: settings.brand_name || 'SK Python Classes',
                        brand_logo_url: settings.brand_logo ? `/storage/${settings.brand_logo}` : null
                    };
                    
                    // Update favicon if available
                    if (settings.favicon) {
                        updateFavicon(`/storage/${settings.favicon}`);
                    }
                }
            } catch (error) {
                console.error('Error fetching brand settings:', error);
            }
        };

        const updateFavicon = (faviconUrl) => {
            let link = document.querySelector("link[rel*='icon']") || document.createElement('link');
            link.type = 'image/x-icon';
            link.rel = 'shortcut icon';
            link.href = faviconUrl;
            document.getElementsByTagName('head')[0].appendChild(link);
        };

        const toggleMobileMenu = () => {
            mobileMenuOpen.value = !mobileMenuOpen.value;
        };

        const closeMobileMenu = () => {
            mobileMenuOpen.value = false;
        };

        const scrollToContact = () => {
            const contactSection = document.getElementById('contact');
            if (contactSection) {
                contactSection.scrollIntoView({ behavior: 'smooth' });
            }
            closeMobileMenu();
        };

        onMounted(() => {
            fetchBrandSettings();
        });

        return {
            mobileMenuOpen,
            brandSettings,
            toggleMobileMenu,
            closeMobileMenu,
            scrollToContact
        };
    }
};
</script>

<style scoped>
.container {
    max-width: 1280px;
    margin: 0 auto;
}

.header-modern {
    backdrop-filter: blur(20px);
    -webkit-backdrop-filter: blur(20px);
}

.logo-container {
    position: relative;
    overflow: hidden;
    border-radius: 12px;
}

.logo-container::before {
    content: '';
    position: absolute;
    inset: 0;
    border-radius: 12px;
    padding: 2px;
    background: linear-gradient(135deg, rgba(59, 130, 246, 0.3), rgba(147, 51, 234, 0.3));
    -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
    -webkit-mask-composite: xor;
    mask-composite: exclude;
    opacity: 0;
    transition: opacity 0.3s ease;
}

.logo-container:hover::before {
    opacity: 1;
}

.nav-link {
    position: relative;
}

.nav-underline {
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%) scaleX(0);
    width: 60%;
    height: 2px;
    background: linear-gradient(90deg, transparent, #3b82f6, transparent);
    transition: transform 0.3s ease;
}

.nav-link:hover .nav-underline {
    transform: translateX(-50%) scaleX(1);
}

.mobile-nav-link {
    position: relative;
    overflow: hidden;
}

.mobile-nav-link::before {
    content: '';
    position: absolute;
    left: 0;
    top: 50%;
    transform: translateY(-50%) translateX(-100%);
    width: 4px;
    height: 60%;
    background: linear-gradient(180deg, #3b82f6, #9333ea);
    border-radius: 0 4px 4px 0;
    transition: transform 0.3s ease;
}

.mobile-nav-link:hover::before {
    transform: translateY(-50%) translateX(0);
}

@keyframes gradient {
    0%, 100% {
        background-position: 0% 50%;
    }
    50% {
        background-position: 100% 50%;
    }
}

.animate-gradient {
    background-size: 200% 200%;
    animation: gradient 3s ease infinite;
}

/* Smooth scroll behavior */
html {
    scroll-behavior: smooth;
}

/* Focus states for accessibility */
.nav-link:focus-visible,
.mobile-nav-link:focus-visible {
    outline: 2px solid #3b82f6;
    outline-offset: 2px;
    border-radius: 8px;
}
</style>

