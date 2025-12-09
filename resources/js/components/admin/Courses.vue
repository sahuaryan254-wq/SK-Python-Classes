<template>
    <div class="w-full overflow-hidden">
        <div class="bg-gradient-to-br from-white to-gray-50 rounded-xl shadow-lg p-4 sm:p-6 border border-gray-100 overflow-hidden">
            <div class="flex flex-col sm:flex-row sm:items-center sm:justify-between mb-4 sm:mb-6 gap-3">
                <div class="flex-1"></div>
                <button 
                    class="bg-gradient-to-r from-indigo-500 to-purple-500 text-white px-4 sm:px-6 py-2 sm:py-3 rounded-xl hover:from-indigo-600 hover:to-purple-600 transition font-medium shadow-lg shadow-indigo-500/30 transform hover:scale-105 text-sm sm:text-base w-full sm:w-auto whitespace-nowrap"
                >
                    Create New Course
                </button>
            </div>
            
            <div class="text-center py-12">
                <div class="w-16 h-16 bg-gradient-to-br from-indigo-500 to-purple-500 rounded-full flex items-center justify-center mx-auto mb-4">
                    <svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253" />
                    </svg>
                </div>
                <h3 class="text-xl font-bold text-gray-800 mb-2">Courses Management</h3>
                <p class="text-gray-600">Create and manage all courses</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Courses'
};
</script>


