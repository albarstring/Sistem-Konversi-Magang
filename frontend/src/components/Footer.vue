<script setup>
import { GraduationCap } from 'lucide-vue-next'
</script>

<template>
  <footer class="bg-gray-900 text-white py-12">
    <div class="max-w-7xl mx-auto px-4">
      <div class="grid md:grid-cols-4 gap-8 mb-8">
        <div>
          <div class="flex items-center space-x-3 mb-4">
            <div class="w-10 h-10 bg-blue-600 rounded-lg flex items-center justify-center">
              <GraduationCap class="w-6 h-6 text-white" />
            </div>
            <div>
              <h3 class="font-bold">Sistem Magang</h3>
              <p class="text-xs text-gray-400">Amikom Yogyakarta</p>
            </div>
          </div>
          <p class="text-gray-400 text-sm">
            Platform terintegrasi untuk mengelola magang mahasiswa
          </p>
        </div>

        <div>
          <h4 class="font-semibold mb-4">Link Cepat</h4>
          <ul class="space-y-2 text-sm text-gray-400">
            <li>
              <a href="#beranda" class="hover:text-white transition-colors">
                Beranda
              </a>
            </li>
            <li>
              <a href="#tentang" class="hover:text-white transition-colors">
                Tentang
              </a>
            </li>
            <li>
              <a href="#fitur" class="hover:text-white transition-colors">
                Fitur
              </a>
            </li>
          </ul>
        </div>

        <div>
          <h4 class="font-semibold mb-4">Kontak</h4>
          <ul class="space-y-2 text-sm text-gray-400">
            <li>Email: magang@amikom.ac.id</li>
            <li>Telepon: (0274) 884201</li>
            <li>Jl. Ring Road Utara, Yogyakarta</li>
          </ul>
        </div>

        <div>
          <h4 class="font-semibold mb-4">Jam Operasional</h4>
          <ul class="space-y-2 text-sm text-gray-400">
            <li>Senin - Jumat: 08.00 - 16.00</li>
            <li>Sabtu: 08.00 - 12.00</li>
            <li>Minggu: Tutup</li>
          </ul>
        </div>
      </div>

      <div class="border-t border-gray-800 pt-8 text-center text-sm text-gray-400">
        <p>&copy; 2026 Universitas Amikom Yogyakarta. All rights reserved.</p>
        <p class="mt-2">Developed by Team Vibe Coder</p>
      </div>
    </div>
  </footer>
</template>
