<template>
    <div class="w-full overflow-hidden space-y-4 sm:space-y-6">
        <!-- Header -->
        <div class="bg-gradient-to-br from-white to-gray-50 rounded-2xl shadow-xl p-4 sm:p-6 border border-gray-100">
            <div class="flex items-center justify-between">
                <div>
                    <h2 class="text-xl sm:text-2xl font-bold text-gray-800 mb-1">My Live Classes</h2>
                    <p class="text-xs sm:text-sm text-gray-600">View and join your scheduled live classes</p>
                </div>
                <div class="hidden sm:flex items-center space-x-2">
                    <div class="w-12 h-12 bg-gradient-to-br from-indigo-500 to-purple-500 rounded-xl flex items-center justify-center shadow-lg">
                        <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 10l4.553-2.276A1 1 0 0121 8.618v6.764a1 1 0 01-1.447.894L15 14M5 18h8a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v8a2 2 0 002 2z" />
                        </svg>
                    </div>
                </div>
            </div>
        </div>

        <!-- Stats Cards -->
        <div v-if="!loading && liveClasses.length > 0" class="grid grid-cols-1 sm:grid-cols-3 gap-4 sm:gap-6">
            <div class="bg-gradient-to-br from-indigo-500 to-purple-500 rounded-2xl shadow-xl p-5 sm:p-6 text-white transform hover:scale-105 transition-all duration-300 border border-indigo-400/20">
                <div class="flex items-center justify-between mb-4">
                    <div>
                        <div class="text-2xl sm:text-3xl font-bold mb-1">{{ upcomingCount }}</div>
                        <div class="text-indigo-100 text-xs sm:text-sm font-medium">Upcoming Classes</div>
                    </div>
                    <div class="w-12 h-12 sm:w-14 sm:h-14 bg-white/20 backdrop-blur-sm rounded-xl flex items-center justify-center">
                        <svg class="w-6 h-6 sm:w-7 sm:h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
                        </svg>
                    </div>
                </div>
            </div>
            <div class="bg-gradient-to-br from-green-500 to-emerald-500 rounded-2xl shadow-xl p-5 sm:p-6 text-white transform hover:scale-105 transition-all duration-300 border border-green-400/20">
                <div class="flex items-center justify-between mb-4">
                    <div>
                        <div class="text-2xl sm:text-3xl font-bold mb-1">{{ todayCount }}</div>
                        <div class="text-green-100 text-xs sm:text-sm font-medium">Today's Classes</div>
                    </div>
                    <div class="w-12 h-12 sm:w-14 sm:h-14 bg-white/20 backdrop-blur-sm rounded-xl flex items-center justify-center">
                        <svg class="w-6 h-6 sm:w-7 sm:h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
                        </svg>
                    </div>
                </div>
            </div>
            <div class="bg-gradient-to-br from-blue-500 to-cyan-500 rounded-2xl shadow-xl p-5 sm:p-6 text-white transform hover:scale-105 transition-all duration-300 border border-blue-400/20">
                <div class="flex items-center justify-between mb-4">
                    <div>
                        <div class="text-2xl sm:text-3xl font-bold mb-1">{{ liveClasses.length }}</div>
                        <div class="text-blue-100 text-xs sm:text-sm font-medium">Total Classes</div>
                    </div>
                    <div class="w-12 h-12 sm:w-14 sm:h-14 bg-white/20 backdrop-blur-sm rounded-xl flex items-center justify-center">
                        <svg class="w-6 h-6 sm:w-7 sm:h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2" />
                        </svg>
                    </div>
                </div>
            </div>
        </div>

        <!-- Live Classes List -->
        <div v-if="loading" class="text-center py-12">
            <div class="inline-block animate-spin rounded-full h-12 w-12 border-b-2 border-indigo-500"></div>
            <p class="mt-4 text-gray-600">Loading live classes...</p>
        </div>

        <div v-else-if="liveClasses.length === 0" class="bg-gradient-to-br from-white to-gray-50 rounded-2xl shadow-xl p-12 text-center border border-gray-100">
            <svg class="w-20 h-20 mx-auto text-gray-400 mb-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 10l4.553-2.276A1 1 0 0121 8.618v6.764a1 1 0 01-1.447.894L15 14M5 18h8a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v8a2 2 0 002 2z" />
            </svg>
            <p class="text-gray-600 text-lg font-medium">No live classes scheduled yet.</p>
            <p class="text-gray-500 text-sm mt-2">Your upcoming live classes will appear here.</p>
        </div>

        <div v-else class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4 sm:gap-6">
            <div 
                v-for="liveClass in liveClasses" 
                :key="liveClass.id"
                class="bg-gradient-to-br from-white to-gray-50 rounded-2xl shadow-xl p-5 sm:p-6 border border-gray-100 hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-1 relative overflow-hidden group"
            >
                <!-- Decorative gradient overlay -->
                <div class="absolute top-0 right-0 w-32 h-32 bg-gradient-to-br from-indigo-100/30 to-purple-100/30 rounded-full -mr-16 -mt-16 group-hover:scale-150 transition-transform duration-500"></div>
                
                <div class="relative z-10">
                    <!-- Status Badge -->
                    <div class="flex items-start justify-between mb-4">
                        <span :class="getStatusClass(liveClass)" class="px-3 py-1.5 rounded-full text-xs font-bold shadow-sm capitalize">
                            {{ getStatusText(liveClass) }}
                        </span>
                        <div class="w-12 h-12 bg-gradient-to-br from-indigo-500 to-purple-500 rounded-xl flex items-center justify-center shadow-lg">
                            <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 10l4.553-2.276A1 1 0 0121 8.618v6.764a1 1 0 01-1.447.894L15 14M5 18h8a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v8a2 2 0 002 2z" />
                            </svg>
                        </div>
                    </div>

                    <!-- Class Title -->
                    <h3 class="text-lg sm:text-xl font-bold text-gray-800 mb-2 line-clamp-2 min-h-[3rem]">{{ liveClass.title }}</h3>
                    
                    <!-- Course Name -->
                    <div class="mb-4 p-3 bg-gray-50 rounded-lg border border-gray-200">
                        <p class="text-xs text-gray-500 mb-1">Course</p>
                        <p class="text-sm font-semibold text-gray-800">{{ liveClass.course?.name || 'General Class' }}</p>
                    </div>

                    <!-- Class Details -->
                    <div class="space-y-2.5 mb-5">
                        <div class="flex items-center text-sm text-gray-700">
                            <svg class="w-5 h-5 mr-2.5 text-indigo-500 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
                            </svg>
                            <div>
                                <span class="text-gray-500 text-xs">Date:</span>
                                <span class="ml-1 font-semibold text-gray-800">{{ formatDate(liveClass.scheduled_date) }}</span>
                            </div>
                        </div>
                        <div class="flex items-center text-sm text-gray-700">
                            <svg class="w-5 h-5 mr-2.5 text-indigo-500 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
                            </svg>
                            <div>
                                <span class="text-gray-500 text-xs">Time:</span>
                                <span class="ml-1 font-semibold text-gray-800">{{ liveClass.start_time }} - {{ liveClass.end_time }}</span>
                            </div>
                        </div>
                        <div v-if="liveClass.instructor" class="flex items-center text-sm text-gray-700">
                            <svg class="w-5 h-5 mr-2.5 text-indigo-500 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z" />
                            </svg>
                            <div>
                                <span class="text-gray-500 text-xs">Instructor:</span>
                                <span class="ml-1 font-semibold text-gray-800">{{ liveClass.instructor }}</span>
                            </div>
                        </div>
                        <div v-if="liveClass.description" class="pt-2 border-t border-gray-200">
                            <p class="text-xs text-gray-500 line-clamp-2">{{ liveClass.description }}</p>
                        </div>
                    </div>

                    <!-- Action Button -->
                    <div v-if="liveClass.meeting_link" class="mt-4">
                        <a 
                            :href="liveClass.meeting_link" 
                            target="_blank"
                            class="w-full inline-flex items-center justify-center px-4 py-3 bg-gradient-to-r from-indigo-500 to-purple-500 text-white rounded-xl text-sm font-semibold hover:from-indigo-600 hover:to-purple-600 transition-all shadow-lg shadow-indigo-500/30 hover:shadow-xl hover:shadow-indigo-500/40"
                        >
                            <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 10l4.553-2.276A1 1 0 0121 8.618v6.764a1 1 0 01-1.447.894L15 14M5 18h8a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v8a2 2 0 002 2z" />
                            </svg>
                            Join Class
                        </a>
                    </div>
                    <div v-else class="mt-4">
                        <button disabled class="w-full px-4 py-3 bg-gray-200 text-gray-500 rounded-xl text-sm font-semibold cursor-not-allowed">
                            <svg class="w-5 h-5 mr-2 inline" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M18.364 18.364A9 9 0 005.636 5.636m12.728 12.728A9 9 0 015.636 5.636m12.728 12.728L5.636 5.636" />
                            </svg>
                            Link Not Available
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import { ref, onMounted, computed } from 'vue';
import axios from 'axios';

export default {
    name: 'StudentLiveClasses',
    setup() {
        const liveClasses = ref([]);
        const loading = ref(true);

        const fetchLiveClasses = async () => {
            try {
                loading.value = true;
                const response = await axios.get('/api/student/live-classes');
                if (response.data.success) {
                    liveClasses.value = response.data.liveClasses || [];
                }
            } catch (error) {
                console.error('Error fetching live classes:', error);
            } finally {
                loading.value = false;
            }
        };

        const formatDate = (dateString) => {
            if (!dateString) return 'N/A';
            const date = new Date(dateString);
            const today = new Date();
            today.setHours(0, 0, 0, 0);
            const classDate = new Date(date);
            classDate.setHours(0, 0, 0, 0);
            
            if (classDate.getTime() === today.getTime()) {
                return 'Today';
            }
            
            const tomorrow = new Date(today);
            tomorrow.setDate(tomorrow.getDate() + 1);
            if (classDate.getTime() === tomorrow.getTime()) {
                return 'Tomorrow';
            }
            
            return date.toLocaleDateString('en-IN', { 
                year: 'numeric', 
                month: 'long', 
                day: 'numeric' 
            });
        };

        const getStatusClass = (liveClass) => {
            if (!liveClass.scheduled_date) return 'bg-gray-100 text-gray-800';
            
            const today = new Date();
            today.setHours(0, 0, 0, 0);
            const classDate = new Date(liveClass.scheduled_date);
            classDate.setHours(0, 0, 0, 0);
            
            if (classDate.getTime() < today.getTime()) {
                return 'bg-gray-100 text-gray-800';
            } else if (classDate.getTime() === today.getTime()) {
                return 'bg-green-100 text-green-800';
            } else {
                return 'bg-blue-100 text-blue-800';
            }
        };

        const getStatusText = (liveClass) => {
            if (!liveClass.scheduled_date) return 'Scheduled';
            
            const today = new Date();
            today.setHours(0, 0, 0, 0);
            const classDate = new Date(liveClass.scheduled_date);
            classDate.setHours(0, 0, 0, 0);
            
            if (classDate.getTime() < today.getTime()) {
                return 'Past';
            } else if (classDate.getTime() === today.getTime()) {
                return 'Today';
            } else {
                return 'Upcoming';
            }
        };

        const upcomingCount = computed(() => {
            const today = new Date();
            today.setHours(0, 0, 0, 0);
            return liveClasses.value.filter(lc => {
                if (!lc.scheduled_date) return false;
                const classDate = new Date(lc.scheduled_date);
                classDate.setHours(0, 0, 0, 0);
                return classDate.getTime() > today.getTime();
            }).length;
        });

        const todayCount = computed(() => {
            const today = new Date();
            today.setHours(0, 0, 0, 0);
            return liveClasses.value.filter(lc => {
                if (!lc.scheduled_date) return false;
                const classDate = new Date(lc.scheduled_date);
                classDate.setHours(0, 0, 0, 0);
                return classDate.getTime() === today.getTime();
            }).length;
        });

        onMounted(() => {
            fetchLiveClasses();
        });

        return {
            liveClasses,
            loading,
            formatDate,
            getStatusClass,
            getStatusText,
            upcomingCount,
            todayCount
        };
    }
};
</script>
