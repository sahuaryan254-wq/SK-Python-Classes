<template>
    <div class="w-full overflow-hidden space-y-4 sm:space-y-6">
        <!-- Header -->
        <div class="bg-gradient-to-br from-white to-gray-50 rounded-2xl shadow-xl p-4 sm:p-6 border border-gray-100">
            <div class="flex items-center justify-between">
                <div>
                    <h2 class="text-xl sm:text-2xl font-bold text-gray-800 mb-1">My Certificates</h2>
                    <p class="text-xs sm:text-sm text-gray-600">View and download your certificates</p>
                </div>
                <div class="hidden sm:flex items-center space-x-2">
                    <div class="w-12 h-12 bg-gradient-to-br from-indigo-500 to-purple-500 rounded-xl flex items-center justify-center shadow-lg">
                        <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z" />
                        </svg>
                    </div>
                </div>
            </div>
        </div>

        <!-- Certificates List -->
        <div v-if="loading" class="text-center py-12">
            <div class="inline-block animate-spin rounded-full h-12 w-12 border-b-2 border-indigo-500"></div>
            <p class="mt-4 text-gray-600">Loading certificates...</p>
        </div>

        <div v-else-if="certificates.length === 0" class="bg-gradient-to-br from-white to-gray-50 rounded-2xl shadow-xl p-12 text-center border border-gray-100">
            <svg class="w-20 h-20 mx-auto text-gray-400 mb-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z" />
            </svg>
            <p class="text-gray-600 text-lg font-medium">No certificates issued yet.</p>
            <p class="text-gray-500 text-sm mt-2">Complete a course to receive your certificate.</p>
        </div>

        <div v-else class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4 sm:gap-6">
            <div 
                v-for="certificate in certificates" 
                :key="certificate.id"
                class="bg-gradient-to-br from-white to-gray-50 rounded-2xl shadow-xl p-5 sm:p-6 border border-gray-100 hover:shadow-2xl transition-all duration-300 transform hover:-translate-y-1 relative overflow-hidden group"
            >
                <!-- Decorative gradient overlay -->
                <div class="absolute top-0 right-0 w-32 h-32 bg-gradient-to-br from-indigo-100/30 to-purple-100/30 rounded-full -mr-16 -mt-16 group-hover:scale-150 transition-transform duration-500"></div>
                
                <div class="relative z-10">
                    <!-- Certificate Icon -->
                    <div class="flex items-start justify-between mb-4">
                        <div class="w-14 h-14 bg-gradient-to-br from-indigo-500 to-purple-500 rounded-xl flex items-center justify-center shadow-lg mb-3">
                            <svg class="w-7 h-7 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z" />
                            </svg>
                        </div>
                        <span :class="getStatusClass(certificate.status)" class="px-3 py-1.5 rounded-full text-xs font-bold shadow-sm capitalize flex-shrink-0">
                            {{ certificate.status }}
                        </span>
                    </div>

                    <!-- Course Name -->
                    <h3 class="text-lg sm:text-xl font-bold text-gray-800 mb-2 line-clamp-2 min-h-[3rem]">{{ certificate.course?.name || 'Course Certificate' }}</h3>
                    
                    <!-- Certificate Number -->
                    <div class="mb-4 p-3 bg-gray-50 rounded-lg border border-gray-200">
                        <p class="text-xs text-gray-500 mb-1">Certificate Number</p>
                        <p class="text-sm font-mono font-semibold text-gray-800 break-all">{{ certificate.certificate_number }}</p>
                    </div>

                    <!-- Date Information -->
                    <div class="space-y-2.5 mb-5 text-sm text-gray-700">
                        <div class="flex items-center">
                            <svg class="w-5 h-5 mr-2.5 text-indigo-500 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
                            </svg>
                            <div>
                                <span class="text-gray-500 text-xs">Issued:</span>
                                <span class="ml-1 font-semibold text-gray-800">{{ formatDate(certificate.issue_date) }}</span>
                            </div>
                        </div>
                        <div v-if="certificate.expiry_date" class="flex items-center">
                            <svg class="w-5 h-5 mr-2.5 text-indigo-500 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
                            </svg>
                            <div>
                                <span class="text-gray-500 text-xs">Expires:</span>
                                <span class="ml-1 font-semibold text-gray-800">{{ formatDate(certificate.expiry_date) }}</span>
                            </div>
                        </div>
                    </div>

                    <!-- Action Buttons -->
                    <div class="flex flex-col sm:flex-row gap-2.5">
                        <button 
                            @click="downloadCertificate(certificate.id)"
                            :disabled="downloadingId === certificate.id"
                            class="flex-1 px-4 py-2.5 bg-gradient-to-r from-indigo-500 to-purple-500 text-white rounded-xl text-sm font-semibold hover:from-indigo-600 hover:to-purple-600 transition-all shadow-lg shadow-indigo-500/30 hover:shadow-xl hover:shadow-indigo-500/40 disabled:opacity-50 disabled:cursor-not-allowed flex items-center justify-center"
                        >
                            <svg v-if="downloadingId !== certificate.id" class="w-4 h-4 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 10v6m0 0l-3-3m3 3l3-3m2 8H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" />
                            </svg>
                            <svg v-else class="w-4 h-4 mr-2 animate-spin" fill="none" viewBox="0 0 24 24">
                                <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                                <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
                            </svg>
                            <span>{{ downloadingId === certificate.id ? 'Downloading...' : 'Download PDF' }}</span>
                        </button>
                        <button 
                            @click="viewCertificate(certificate)"
                            class="px-4 py-2.5 bg-white border-2 border-gray-200 text-gray-700 rounded-xl text-sm font-semibold hover:bg-gray-50 hover:border-indigo-300 transition-all flex items-center justify-center"
                        >
                            <svg class="w-4 h-4 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z" />
                            </svg>
                            View
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- View Certificate Modal -->
        <div v-if="showViewModal" class="fixed inset-0 bg-black bg-opacity-50 z-50 flex items-center justify-center p-4" @click.self="closeViewModal">
            <div class="bg-white rounded-2xl shadow-2xl max-w-2xl w-full max-h-[90vh] overflow-y-auto">
                <div class="sticky top-0 bg-gradient-to-r from-indigo-500 to-purple-500 px-6 py-4 flex items-center justify-between rounded-t-2xl">
                    <h3 class="text-xl font-bold text-white">Certificate Details</h3>
                    <button @click="closeViewModal" class="text-white hover:text-gray-200 transition">
                        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                        </svg>
                    </button>
                </div>
                <div v-if="viewingCertificate" class="p-6">
                    <div class="text-center mb-6">
                        <div class="w-20 h-20 bg-gradient-to-br from-indigo-500 to-purple-500 rounded-full flex items-center justify-center mx-auto mb-4 shadow-lg">
                            <svg class="w-10 h-10 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z" />
                            </svg>
                        </div>
                        <h4 class="text-2xl font-bold text-gray-800 mb-2">{{ viewingCertificate.course?.name || 'Course Certificate' }}</h4>
                        <p class="text-gray-600">Certificate of Completion</p>
                    </div>
                    
                    <div class="space-y-4">
                        <div class="bg-gray-50 rounded-xl p-4 border border-gray-200">
                            <p class="text-sm text-gray-500 mb-1">Certificate Number</p>
                            <p class="text-lg font-mono font-bold text-gray-800">{{ viewingCertificate.certificate_number }}</p>
                        </div>
                        
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div class="bg-gray-50 rounded-xl p-4 border border-gray-200">
                                <p class="text-sm text-gray-500 mb-1">Issue Date</p>
                                <p class="text-base font-semibold text-gray-800">{{ formatDate(viewingCertificate.issue_date) }}</p>
                            </div>
                            <div v-if="viewingCertificate.expiry_date" class="bg-gray-50 rounded-xl p-4 border border-gray-200">
                                <p class="text-sm text-gray-500 mb-1">Expiry Date</p>
                                <p class="text-base font-semibold text-gray-800">{{ formatDate(viewingCertificate.expiry_date) }}</p>
                            </div>
                        </div>
                        
                        <div class="bg-gray-50 rounded-xl p-4 border border-gray-200">
                            <p class="text-sm text-gray-500 mb-1">Status</p>
                            <span :class="getStatusClass(viewingCertificate.status)" class="inline-flex items-center px-3 py-1.5 rounded-full text-sm font-bold shadow-sm capitalize">
                                {{ viewingCertificate.status }}
                            </span>
                        </div>
                    </div>
                    
                    <div class="mt-6 flex flex-col sm:flex-row gap-3">
                        <button 
                            @click="downloadCertificate(viewingCertificate.id)"
                            :disabled="downloadingId === viewingCertificate.id"
                            class="flex-1 px-4 py-3 bg-gradient-to-r from-indigo-500 to-purple-500 text-white rounded-xl text-sm font-semibold hover:from-indigo-600 hover:to-purple-600 transition-all shadow-lg disabled:opacity-50 disabled:cursor-not-allowed flex items-center justify-center"
                        >
                            <svg v-if="downloadingId !== viewingCertificate.id" class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 10v6m0 0l-3-3m3 3l3-3m2 8H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" />
                            </svg>
                            <svg v-else class="w-5 h-5 mr-2 animate-spin" fill="none" viewBox="0 0 24 24">
                                <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                                <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
                            </svg>
                            <span>{{ downloadingId === viewingCertificate.id ? 'Downloading...' : 'Download PDF' }}</span>
                        </button>
                        <button 
                            @click="verifyCertificate(viewingCertificate.certificate_number)"
                            class="px-4 py-3 bg-white border-2 border-indigo-500 text-indigo-600 rounded-xl text-sm font-semibold hover:bg-indigo-50 transition-all flex items-center justify-center"
                        >
                            <svg class="w-5 h-5 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z" />
                            </svg>
                            Verify Certificate
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import { ref, onMounted } from 'vue';
import { useRouter } from 'vue-router';
import axios from 'axios';

export default {
    name: 'StudentCertificates',
    setup() {
        const router = useRouter();
        const certificates = ref([]);
        const loading = ref(true);
        const downloadingId = ref(null);
        const showViewModal = ref(false);
        const viewingCertificate = ref(null);

        const fetchCertificates = async () => {
            try {
                loading.value = true;
                const response = await axios.get('/api/student/certificates');
                if (response.data.success) {
                    certificates.value = response.data.certificates || [];
                }
            } catch (error) {
                console.error('Error fetching certificates:', error);
            } finally {
                loading.value = false;
            }
        };

        const formatDate = (dateString) => {
            if (!dateString) return 'N/A';
            const date = new Date(dateString);
            return date.toLocaleDateString('en-IN', { 
                year: 'numeric', 
                month: 'long', 
                day: 'numeric' 
            });
        };

        const getStatusClass = (status) => {
            const classes = {
                'active': 'bg-green-100 text-green-800',
                'revoked': 'bg-red-100 text-red-800'
            };
            return classes[status] || 'bg-gray-100 text-gray-800';
        };

        const downloadCertificate = async (certificateId) => {
            try {
                downloadingId.value = certificateId;
                const response = await axios.get(`/api/student/certificates/${certificateId}/download`, {
                    responseType: 'blob'
                });
                const url = window.URL.createObjectURL(new Blob([response.data]));
                const link = document.createElement('a');
                link.href = url;
                
                // Get certificate number for filename
                const certificate = certificates.value.find(c => c.id === certificateId);
                const filename = certificate ? `certificate-${certificate.certificate_number}.pdf` : `certificate-${certificateId}.pdf`;
                
                link.setAttribute('download', filename);
                document.body.appendChild(link);
                link.click();
                link.remove();
                window.URL.revokeObjectURL(url);
            } catch (error) {
                console.error('Error downloading certificate:', error);
                alert('Failed to download certificate. Please try again.');
            } finally {
                downloadingId.value = null;
            }
        };

        const viewCertificate = (certificate) => {
            viewingCertificate.value = certificate;
            showViewModal.value = true;
        };

        const closeViewModal = () => {
            showViewModal.value = false;
            viewingCertificate.value = null;
        };

        const verifyCertificate = (certificateNumber) => {
            router.push(`/certificateverify/${certificateNumber}`);
            closeViewModal();
        };

        onMounted(() => {
            fetchCertificates();
        });

        return {
            certificates,
            loading,
            downloadingId,
            showViewModal,
            viewingCertificate,
            formatDate,
            getStatusClass,
            downloadCertificate,
            viewCertificate,
            closeViewModal,
            verifyCertificate
        };
    }
};
</script>
