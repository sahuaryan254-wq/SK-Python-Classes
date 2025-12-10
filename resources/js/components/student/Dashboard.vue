<template>
    <div class="w-full overflow-hidden space-y-6">
        <!-- Stats Cards -->
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4 sm:gap-6">
            <div class="stat-card bg-gradient-to-br from-indigo-500 to-purple-500 rounded-2xl shadow-xl p-6 text-white transform hover:scale-105 transition-all duration-300 border border-indigo-400/20">
                <div class="flex items-center justify-between mb-4">
                    <div>
                        <div class="text-3xl sm:text-4xl font-bold mb-1">{{ stats.enrolledCourses }}</div>
                        <div class="text-indigo-100 text-sm sm:text-base font-medium">Enrolled Courses</div>
                    </div>
                    <div class="w-14 h-14 bg-white/20 backdrop-blur-sm rounded-xl flex items-center justify-center">
                        <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253" />
                        </svg>
                    </div>
                </div>
            </div>

            <div class="stat-card bg-gradient-to-br from-green-500 to-emerald-500 rounded-2xl shadow-xl p-6 text-white transform hover:scale-105 transition-all duration-300 border border-green-400/20">
                <div class="flex items-center justify-between mb-4">
                    <div>
                        <div class="text-3xl sm:text-4xl font-bold mb-1">{{ stats.certificates }}</div>
                        <div class="text-green-100 text-sm sm:text-base font-medium">Certificates</div>
                    </div>
                    <div class="w-14 h-14 bg-white/20 backdrop-blur-sm rounded-xl flex items-center justify-center">
                        <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z" />
                        </svg>
                    </div>
                </div>
            </div>

            <div class="stat-card bg-gradient-to-br from-blue-500 to-cyan-500 rounded-2xl shadow-xl p-6 text-white transform hover:scale-105 transition-all duration-300 border border-blue-400/20">
                <div class="flex items-center justify-between mb-4">
                    <div>
                        <div class="text-3xl sm:text-4xl font-bold mb-1">{{ stats.totalPayments }}</div>
                        <div class="text-blue-100 text-sm sm:text-base font-medium">Total Payments</div>
                    </div>
                    <div class="w-14 h-14 bg-white/20 backdrop-blur-sm rounded-xl flex items-center justify-center">
                        <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 9V7a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2m2 4h10a2 2 0 002-2v-6a2 2 0 00-2-2H9a2 2 0 00-2 2v6a2 2 0 002 2zm7-5a2 2 0 11-4 0 2 2 0 014 0z" />
                        </svg>
                    </div>
                </div>
            </div>

            <div class="stat-card bg-gradient-to-br from-orange-500 to-red-500 rounded-2xl shadow-xl p-6 text-white transform hover:scale-105 transition-all duration-300 border border-orange-400/20">
                <div class="flex items-center justify-between mb-4">
                    <div>
                        <div class="text-3xl sm:text-4xl font-bold mb-1">{{ stats.upcomingClasses }}</div>
                        <div class="text-orange-100 text-sm sm:text-base font-medium">Upcoming Classes</div>
                    </div>
                    <div class="w-14 h-14 bg-white/20 backdrop-blur-sm rounded-xl flex items-center justify-center">
                        <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 10l4.553-2.276A1 1 0 0121 8.618v6.764a1 1 0 01-1.447.894L15 14M5 18h8a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v8a2 2 0 002 2z" />
                        </svg>
                    </div>
                </div>
            </div>
        </div>

        <!-- Upcoming Live Classes -->
        <div class="bg-gradient-to-br from-white to-gray-50 rounded-2xl shadow-xl p-4 sm:p-6 border border-gray-100">
            <div class="flex items-center justify-between mb-4 sm:mb-6">
                <div>
                    <h2 class="text-xl sm:text-2xl font-bold text-gray-800 mb-1">Upcoming Live Classes</h2>
                    <p class="text-sm text-gray-600 hidden sm:block">Your scheduled live classes</p>
                </div>
            </div>
            <div v-if="loading" class="text-center py-12">
                <div class="inline-block animate-spin rounded-full h-12 w-12 border-b-2 border-indigo-500"></div>
            </div>
            <div v-else-if="upcomingClasses.length === 0" class="text-center py-12">
                <svg class="w-16 h-16 mx-auto text-gray-400 mb-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 10l4.553-2.276A1 1 0 0121 8.618v6.764a1 1 0 01-1.447.894L15 14M5 18h8a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v8a2 2 0 002 2z" />
                </svg>
                <p class="text-gray-600 text-lg">No upcoming live classes scheduled.</p>
            </div>
            <div v-else class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4 sm:gap-6">
                <div 
                    v-for="liveClass in upcomingClasses" 
                    :key="liveClass.id"
                    class="bg-white rounded-xl p-4 sm:p-5 border-2 border-gray-200 hover:border-indigo-500 transition-all duration-300 shadow-sm hover:shadow-lg transform hover:-translate-y-1"
                >
                    <div class="flex items-start justify-between mb-3">
                        <div class="flex-1 min-w-0">
                            <h3 class="font-bold text-gray-800 mb-1 text-sm sm:text-base truncate">{{ liveClass.title }}</h3>
                            <p class="text-xs sm:text-sm text-gray-600 truncate">{{ liveClass.course?.name || 'General' }}</p>
                        </div>
                    </div>
                    <div class="space-y-2 text-xs sm:text-sm mb-4">
                        <div class="flex items-center text-gray-700">
                            <svg class="w-4 h-4 mr-2 text-indigo-500 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
                            </svg>
                            <span class="truncate">{{ formatDate(liveClass.scheduled_date) }}</span>
                        </div>
                        <div class="flex items-center text-gray-700">
                            <svg class="w-4 h-4 mr-2 text-indigo-500 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
                            </svg>
                            <span>{{ liveClass.start_time }} - {{ liveClass.end_time }}</span>
                        </div>
                    </div>
                    <div v-if="liveClass.meeting_link" class="mt-4">
                        <a 
                            :href="liveClass.meeting_link" 
                            target="_blank"
                            class="w-full inline-flex items-center justify-center px-3 py-2 bg-gradient-to-r from-indigo-500 to-purple-500 text-white rounded-lg text-xs sm:text-sm font-medium hover:from-indigo-600 hover:to-purple-600 transition shadow-md shadow-indigo-500/30"
                        >
                            <svg class="w-4 h-4 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 10l4.553-2.276A1 1 0 0121 8.618v6.764a1 1 0 01-1.447.894L15 14M5 18h8a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v8a2 2 0 002 2z" />
                            </svg>
                            Join Class
                        </a>
                    </div>
                    <div v-else class="mt-4">
                        <button disabled class="w-full px-3 py-2 bg-gray-200 text-gray-500 rounded-lg text-xs sm:text-sm font-medium cursor-not-allowed">
                            Link Not Available
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Recent Payments -->
        <div class="bg-gradient-to-br from-white to-gray-50 rounded-2xl shadow-xl p-4 sm:p-6 border border-gray-100">
            <div class="flex items-center justify-between mb-4 sm:mb-6">
                <div>
                    <h2 class="text-xl sm:text-2xl font-bold text-gray-800 mb-1">Recent Payments</h2>
                    <p class="text-sm text-gray-600 hidden sm:block">Your latest payment transactions</p>
                </div>
            </div>
            <div v-if="loading" class="text-center py-8">
                <div class="inline-block animate-spin rounded-full h-8 w-8 border-b-2 border-indigo-500"></div>
            </div>
            <div v-else-if="recentPayments.length === 0" class="text-center py-8 text-gray-500">
                <p>No payment records found.</p>
            </div>
            <template v-else>
                <!-- Desktop Table View -->
                <div class="hidden lg:block overflow-x-auto">
                    <table class="w-full">
                        <thead>
                            <tr class="border-b-2 border-gray-200 bg-gray-50">
                                <th class="text-left py-4 px-6 text-sm font-bold text-gray-700">Course</th>
                                <th class="text-left py-4 px-6 text-sm font-bold text-gray-700">Amount</th>
                                <th class="text-left py-4 px-6 text-sm font-bold text-gray-700">Status</th>
                                <th class="text-left py-4 px-6 text-sm font-bold text-gray-700">Date</th>
                            </tr>
                        </thead>
                        <tbody class="bg-white divide-y divide-gray-100">
                            <tr v-for="payment in recentPayments" :key="payment.id" class="hover:bg-gray-50 transition-colors">
                                <td class="py-5 px-6 text-sm font-semibold text-gray-900">{{ payment.course?.name || 'N/A' }}</td>
                                <td class="py-5 px-6 text-sm font-bold text-indigo-600">₹{{ payment.amount }}</td>
                                <td class="py-5 px-6">
                                    <span :class="getStatusClass(payment.status)" class="inline-flex items-center px-3 py-1.5 rounded-full text-xs font-bold shadow-sm capitalize">
                                        {{ payment.status }}
                                    </span>
                                </td>
                                <td class="py-5 px-6 text-sm text-gray-600">{{ formatDate(payment.payment_date) }}</td>
                            </tr>
                        </tbody>
                    </table>
                </div>

                <!-- Mobile Card View -->
                <div class="lg:hidden space-y-3">
                    <div v-for="payment in recentPayments" :key="payment.id" class="bg-white rounded-xl shadow-md p-4 border border-gray-200">
                        <div class="flex items-start justify-between mb-2">
                            <div class="flex-1">
                                <h3 class="font-bold text-gray-900 text-sm mb-1">{{ payment.course?.name || 'N/A' }}</h3>
                                <p class="text-xs text-gray-500">{{ formatDate(payment.payment_date) }}</p>
                            </div>
                            <span :class="getStatusClass(payment.status)" class="inline-flex items-center px-2.5 py-1 rounded-full text-xs font-bold shadow-sm capitalize">
                                {{ payment.status }}
                            </span>
                        </div>
                        <div class="flex justify-between items-center pt-2 border-t border-gray-100">
                            <span class="text-xs text-gray-600">Amount:</span>
                            <span class="text-sm font-bold text-indigo-600">₹{{ payment.amount }}</span>
                        </div>
                    </div>
                </div>
            </template>
        </div>
    </div>
</template>

<script>
import { ref, onMounted } from 'vue';
import axios from 'axios';

export default {
    name: 'StudentDashboard',
    setup() {
        const stats = ref({
            enrolledCourses: 0,
            certificates: 0,
            totalPayments: 0,
            upcomingClasses: 0
        });
        const upcomingClasses = ref([]);
        const recentPayments = ref([]);
        const loading = ref(true);

        const fetchDashboardData = async () => {
            try {
                loading.value = true;
                const response = await axios.get('/api/student/dashboard');
                if (response.data.success) {
                    stats.value = response.data.stats;
                    upcomingClasses.value = response.data.upcomingClasses || [];
                    recentPayments.value = response.data.recentPayments || [];
                }
            } catch (error) {
                console.error('Error fetching dashboard data:', error);
            } finally {
                loading.value = false;
            }
        };

        const formatDate = (dateString) => {
            if (!dateString) return 'N/A';
            const date = new Date(dateString);
            return date.toLocaleDateString('en-IN', { 
                year: 'numeric', 
                month: 'short', 
                day: 'numeric' 
            });
        };

        const getStatusClass = (status) => {
            const classes = {
                'paid': 'bg-green-100 text-green-800',
                'pending': 'bg-yellow-100 text-yellow-800',
                'failed': 'bg-red-100 text-red-800',
                'refunded': 'bg-gray-100 text-gray-800'
            };
            return classes[status] || 'bg-gray-100 text-gray-800';
        };

        onMounted(() => {
            fetchDashboardData();
        });

        return {
            stats,
            upcomingClasses,
            recentPayments,
            loading,
            formatDate,
            getStatusClass
        };
    }
};
</script>

<style scoped>
.stat-card {
    transition: transform 0.3s ease;
}
</style>

