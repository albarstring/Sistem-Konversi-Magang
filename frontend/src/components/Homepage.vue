<script setup>
import { Briefcase, Users, TrendingUp, CheckCircle, ArrowRight, Building } from 'lucide-vue-next'

defineProps({
  onLoginClick: Function
})
</script>

<template>
  <div class="min-h-screen bg-white">
    <!-- Hero Section -->
    <section id="beranda" class="bg-gradient-to-br from-blue-50 to-indigo-100 pt-36 pb-20">
      <div class="max-w-7xl mx-auto px-4">
        <div class="grid md:grid-cols-2 gap-12 items-center">
          <div>
            <h1 class="text-5xl font-bold text-gray-900 mb-6">
              Kelola Magang Mahasiswa dengan Mudah
            </h1>
            <p class="text-xl text-gray-700 mb-8">
              Platform terintegrasi untuk mengelola seluruh proses magang, dari pencarian lowongan hingga
              pelaporan dan evaluasi.
            </p>
            <div class="flex flex-col sm:flex-row gap-4">
              <button
                @click="onLoginClick"
                class="flex items-center justify-center space-x-2 px-8 py-4 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors text-lg font-medium"
              >
                <span>Mulai Sekarang</span>
                <ArrowRight class="w-5 h-5" />
              </button>
              <button class="px-8 py-4 border-2 border-blue-600 text-blue-600 rounded-lg hover:bg-blue-50 transition-colors text-lg font-medium">
                Pelajari Lebih Lanjut
              </button>
            </div>
          </div>
          <div class="hidden md:block">
            <div class="bg-white rounded-2xl shadow-2xl p-8">
              <div class="space-y-6">
                <div class="flex items-center space-x-4">
                  <div class="w-12 h-12 bg-blue-100 rounded-lg flex items-center justify-center">
                    <Users class="w-6 h-6 text-blue-600" />
                  </div>
                  <div>
                    <p class="text-2xl font-bold text-gray-900">150+</p>
                    <p class="text-gray-600">Mahasiswa Magang</p>
                  </div>
                </div>
                <div class="flex items-center space-x-4">
                  <div class="w-12 h-12 bg-green-100 rounded-lg flex items-center justify-center">
                    <Building class="w-6 h-6 text-green-600" />
                  </div>
                  <div>
                    <p class="text-2xl font-bold text-gray-900">50+</p>
                    <p class="text-gray-600">Perusahaan Mitra</p>
                  </div>
                </div>
                <div class="flex items-center space-x-4">
                  <div class="w-12 h-12 bg-purple-100 rounded-lg flex items-center justify-center">
                    <Briefcase class="w-6 h-6 text-purple-600" />
                  </div>
                  <div>
                    <p class="text-2xl font-bold text-gray-900">80+</p>
                    <p class="text-gray-600">Lowongan Tersedia</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section id="tentang" class="py-20">
      <div class="max-w-7xl mx-auto px-4">
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold text-gray-900 mb-4">Tentang Sistem Magang</h2>
          <p class="text-xl text-gray-600 max-w-3xl mx-auto">
            Platform komprehensif yang menghubungkan mahasiswa, dosen pembimbing, admin prodi, dan perusahaan
            mitra dalam satu ekosistem magang yang terintegrasi.
          </p>
        </div>

        <div class="grid md:grid-cols-4 gap-8">
          <div class="text-center">
            <div class="w-16 h-16 bg-blue-100 rounded-full flex items-center justify-center mx-auto mb-4">
              <Users class="w-8 h-8 text-blue-600" />
            </div>
            <h3 class="text-lg font-semibold text-gray-900 mb-2">Mahasiswa</h3>
            <p class="text-gray-600">Cari lowongan, daftar magang, dan kelola laporan dengan mudah</p>
          </div>

          <div class="text-center">
            <div class="w-16 h-16 bg-green-100 rounded-full flex items-center justify-center mx-auto mb-4">
              <GraduationCap class="w-8 h-8 text-green-600" />
            </div>
            <h3 class="text-lg font-semibold text-gray-900 mb-2">Dosen Pembimbing</h3>
            <p class="text-gray-600">Monitor dan review perkembangan mahasiswa bimbingan</p>
          </div>

          <div class="text-center">
            <div class="w-16 h-16 bg-purple-100 rounded-full flex items-center justify-center mx-auto mb-4">
              <CheckCircle class="w-8 h-8 text-purple-600" />
            </div>
            <h3 class="text-lg font-semibold text-gray-900 mb-2">Admin Prodi</h3>
            <p class="text-gray-600">Kelola data, validasi, dan monitoring seluruh sistem</p>
          </div>

          <div class="text-center">
            <div class="w-16 h-16 bg-orange-100 rounded-full flex items-center justify-center mx-auto mb-4">
              <Building class="w-8 h-8 text-orange-600" />
            </div>
            <h3 class="text-lg font-semibold text-gray-900 mb-2">Mitra Perusahaan</h3>
            <p class="text-gray-600">Post lowongan dan kelola mahasiswa magang</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Features Section -->
    <section id="fitur" class="py-20 bg-gray-50">
      <div class="max-w-7xl mx-auto px-4">
        <div class="text-center mb-16">
          <h2 class="text-4xl font-bold text-gray-900 mb-4">Fitur Unggulan</h2>
          <p class="text-xl text-gray-600">Semua yang Anda butuhkan untuk mengelola magang</p>
        </div>

        <div class="grid md:grid-cols-3 gap-8">
          <div class="bg-white rounded-xl shadow-lg p-6">
            <div class="w-12 h-12 bg-blue-100 rounded-lg flex items-center justify-center mb-4">
              <Briefcase class="w-6 h-6 text-blue-600" />
            </div>
            <h3 class="text-xl font-semibold text-gray-900 mb-3">Pencarian Lowongan</h3>
            <p class="text-gray-600">
              Temukan lowongan magang yang sesuai dengan minat dan keahlian dengan fitur pencarian dan filter
              yang canggih.
            </p>
          </div>

          <div class="bg-white rounded-xl shadow-lg p-6">
            <div class="w-12 h-12 bg-green-100 rounded-lg flex items-center justify-center mb-4">
              <CheckCircle class="w-6 h-6 text-green-600" />
            </div>
            <h3 class="text-xl font-semibold text-gray-900 mb-3">Approval Workflow</h3>
            <p class="text-gray-600">
              Sistem persetujuan otomatis dari admin dan perusahaan untuk memastikan proses yang terstruktur.
            </p>
          </div>

          <div class="bg-white rounded-xl shadow-lg p-6">
            <div class="w-12 h-12 bg-purple-100 rounded-lg flex items-center justify-center mb-4">
              <TrendingUp class="w-6 h-6 text-purple-600" />
            </div>
            <h3 class="text-xl font-semibold text-gray-900 mb-3">Tracking Progress</h3>
            <p class="text-gray-600">
              Pantau perkembangan magang secara real-time dengan visualisasi progress dan laporan bulanan.
            </p>
          </div>

          <div class="bg-white rounded-xl shadow-lg p-6">
            <div class="w-12 h-12 bg-orange-100 rounded-lg flex items-center justify-center mb-4">
              <Users class="w-6 h-6 text-orange-600" />
            </div>
            <h3 class="text-xl font-semibold text-gray-900 mb-3">Role-Based Access</h3>
            <p class="text-gray-600">
              Setiap pengguna memiliki akses sesuai perannya untuk menjaga keamanan dan privasi data.
            </p>
          </div>

          <div class="bg-white rounded-xl shadow-lg p-6">
            <div class="w-12 h-12 bg-red-100 rounded-lg flex items-center justify-center mb-4">
              <GraduationCap class="w-6 h-6 text-red-600" />
            </div>
            <h3 class="text-xl font-semibold text-gray-900 mb-3">Validasi Akademik</h3>
            <p class="text-gray-600">
              Sistem otomatis memvalidasi IPK dan semester untuk memastikan mahasiswa memenuhi syarat.
            </p>
          </div>

          <div class="bg-white rounded-xl shadow-lg p-6">
            <div class="w-12 h-12 bg-indigo-100 rounded-lg flex items-center justify-center mb-4">
              <Briefcase class="w-6 h-6 text-indigo-600" />
            </div>
            <h3 class="text-xl font-semibold text-gray-900 mb-3">Laporan Digital</h3>
            <p class="text-gray-600">
              Submit dan review laporan bulanan secara digital dengan feedback langsung dari pembimbing.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA Section -->
    <section id="kontak" class="py-20">
      <div class="max-w-7xl mx-auto px-4">
        <div class="bg-gradient-to-r from-blue-600 to-indigo-600 rounded-2xl shadow-2xl p-12 text-center text-white">
          <h2 class="text-4xl font-bold mb-4">Siap Memulai?</h2>
          <p class="text-xl mb-8 opacity-90">
            Bergabunglah dengan ratusan mahasiswa yang telah menemukan pengalaman magang terbaik mereka
          </p>
          <button
            @click="onLoginClick"
            class="px-8 py-4 bg-white text-blue-600 rounded-lg hover:bg-gray-100 transition-colors text-lg font-medium inline-flex items-center space-x-2"
          >
            <span>Login Sekarang</span>
            <ArrowRight class="w-5 h-5" />
          </button>
        </div>
      </div>
    </section>
  </div>
</template>
