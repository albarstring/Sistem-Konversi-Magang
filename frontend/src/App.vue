<script setup>
import { ref } from 'vue'
import Homepage from './components/Homepage.vue'
import LowonganPage from './components/LowonganPage.vue'
import Perusahaan from './components/Perusahaan.vue'
import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'

const currentPage = ref('home')

const handleNavigate = (page) => {
  currentPage.value = page
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

const handleLoginClick = () => {
  alert('Fitur login akan segera tersedia')
}
</script>

<template>
  <Navbar
    :currentPage="currentPage"
    :onLoginClick="handleLoginClick"
    :onNavigate="handleNavigate"
  />

  <Homepage v-if="currentPage === 'home'" :onLoginClick="handleLoginClick" />
  <LowonganPage v-else-if="currentPage === 'lowongan'" :onLoginClick="handleLoginClick" />
  <Perusahaan v-else-if="currentPage === 'perusahaan'" :onLoginClick="handleLoginClick" />

  <Footer />
</template>
