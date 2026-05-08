<script setup>
import { GraduationCap } from 'lucide-vue-next'

const props = defineProps({
  currentPage: {
    type: String,
    default: 'home',
  },
  onLoginClick: {
    type: Function,
    default: () => {},
  },
  onNavigate: {
    type: Function,
    default: () => {},
  },
})

const goToHome = () => {
  props.onNavigate('home')
}

const goToLowongan = () => {
  props.onNavigate('lowongan')
}

const goToPerusahaan = () => {
  props.onNavigate('perusahaan')
}
</script>

<template>
  <nav class="fixed top-5 w-full z-50">
    <div class="max-w-7xl mx-auto px-10">
      <div
        class="rounded-2xl border border-gray-200 bg-white/90 shadow-lg backdrop-blur-md"
      >
        <div class="flex items-center h-16 px-4">
          <div class="flex items-center space-x-3">
            <div
              class="w-10 h-10 bg-blue-600 rounded-lg flex items-center justify-center"
            >
              <GraduationCap class="w-6 h-6 text-white" />
            </div>

            <div>
              <h1 class="font-bold text-lg text-gray-900">Lowongan Magang</h1>
              <p class="text-xs text-gray-600">Universitas Amikom Yogyakarta</p>
            </div>
          </div>

          <div class="hidden md:flex items-center space-x-8 ml-12">
            <button
              type="button"
              @click="goToHome"
              class="text-gray-700 hover:text-blue-600 transition-colors"
            >
              Beranda
            </button>

            <button
              type="button"
              @click="goToLowongan"
              class="text-gray-700 hover:text-blue-600 transition-colors"
            >
              Lowongan
            </button>

            <button
              type="button"
              @click="goToPerusahaan"
              class="text-gray-700 hover:text-blue-600 transition-colors"
            >
              Perusahaan
            </button>
          </div>

          <div class="hidden md:flex items-center space-x-3 ml-auto">
            <button
              @click="props.onLoginClick"
              class="px-6 py-2 border border-blue-600 text-blue-600 rounded-lg hover:bg-blue-50 transition-colors"
            >
              Login
            </button>

            <button
              @click="props.onLoginClick"
              class="px-6 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors"
            >
              Register
            </button>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>
