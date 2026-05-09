<script setup>
import { computed, ref } from 'vue'
import {
  Building,
  MapPin,
  Users,
  Briefcase,
  Globe,
  Mail,
  Phone,
  Star,
  X,
} from 'lucide-vue-next'

const props = defineProps({
  onLoginClick: {
    type: Function,
    default: () => {},
  },
})

const selectedCompany = ref(null)
const selectedCategory = ref('all')

const companies = [
  {
    id: '1',
    name: 'PT. Tech Indonesia',
    category: 'Technology',
    location: 'Yogyakarta',
    description:
      'PT. Tech Indonesia adalah perusahaan teknologi terkemuka yang fokus pada pengembangan solusi digital untuk berbagai industri. Kami berkomitmen untuk menciptakan inovasi dan memberikan pengalaman terbaik bagi klien.',
    website: 'https://techindonesia.com',
    email: 'hr@techindonesia.com',
    phone: '0274-123456',
    address: 'Jl. Kaliurang KM 14.5, Sleman, Yogyakarta',
    activeLowongan: 5,
    totalInterns: 24,
    rating: 4.8,
    established: '2015',
  },
  {
    id: '2',
    name: 'PT. Digital Solution',
    category: 'Technology',
    location: 'Jakarta',
    description:
      'Perusahaan software development yang mengembangkan aplikasi mobile dan web untuk klien enterprise. Dengan pengalaman lebih dari 8 tahun, kami telah melayani ratusan klien di seluruh Indonesia.',
    website: 'https://digitalsolution.co.id',
    email: 'contact@digitalsolution.com',
    phone: '021-987654',
    address: 'Jl. Sudirman No. 100, Jakarta Selatan',
    activeLowongan: 3,
    totalInterns: 18,
    rating: 4.6,
    established: '2016',
  },
  {
    id: '3',
    name: 'Creative Studio',
    category: 'Design',
    location: 'Bandung',
    description:
      'Studio kreatif yang berfokus pada design, branding, dan digital marketing. Kami membantu brand untuk berkembang melalui strategi kreatif yang inovatif.',
    website: 'https://creativestudio.id',
    email: 'hello@creativestudio.id',
    phone: '022-567890',
    address: 'Jl. Dago No. 45, Bandung',
    activeLowongan: 2,
    totalInterns: 12,
    rating: 4.7,
    established: '2018',
  },
  {
    id: '4',
    name: 'PT. Data Insights',
    category: 'Data Science',
    location: 'Yogyakarta',
    description:
      'Perusahaan konsultan data yang membantu bisnis dalam membuat keputusan berbasis data. Kami menyediakan layanan analytics, machine learning, dan business intelligence.',
    website: 'https://datainsights.co.id',
    email: 'info@datainsights.co.id',
    phone: '0274-789012',
    address: 'Jl. Seturan Raya No. 20, Sleman, Yogyakarta',
    activeLowongan: 2,
    totalInterns: 8,
    rating: 4.9,
    established: '2019',
  },
  {
    id: '5',
    name: 'PT. Marketing Hub',
    category: 'Marketing',
    location: 'Jakarta',
    description:
      'Agency digital marketing yang membantu brand untuk tumbuh di era digital. Kami spesialis dalam social media marketing, content creation, dan digital advertising.',
    website: 'https://marketinghub.id',
    email: 'contact@marketinghub.id',
    phone: '021-345678',
    address: 'Jl. Gatot Subroto No. 88, Jakarta Selatan',
    activeLowongan: 4,
    totalInterns: 15,
    rating: 4.5,
    established: '2017',
  },
  {
    id: '6',
    name: 'PT. Inovasi Digital',
    category: 'Technology',
    location: 'Semarang',
    description:
      'Startup teknologi yang berfokus pada IoT dan smart solutions. Kami mengembangkan produk-produk inovatif untuk smart city dan smart home.',
    website: 'https://inovasidigital.com',
    email: 'team@inovasidigital.com',
    phone: '024-456789',
    address: 'Jl. Pemuda No. 150, Semarang',
    activeLowongan: 3,
    totalInterns: 10,
    rating: 4.6,
    established: '2020',
  },
]

const categories = ['all', 'Technology', 'Design', 'Data Science', 'Marketing']

const filteredCompanies = computed(() => {
  if (selectedCategory.value === 'all') {
    return companies
  }

  return companies.filter((item) => item.category === selectedCategory.value)
})

const closeDetail = () => {
  selectedCompany.value = null
}

const openDetail = (company) => {
  selectedCompany.value = company
}
</script>

<template>
  <div class="min-h-screen bg-gray-50">
    <div class="bg-[#008BFF] pt-36 py-12 pb-12 pt-36 text-white">
      <div class="mx-auto max-w-7xl px-4 lg:px-10">
        <h1 class="mb-4 text-4xl font-bold">Perusahaan Mitra</h1>
        <p class="text-xl opacity-90">Temukan perusahaan terbaik untuk pengalaman magang Anda</p>
        <div class="mt-6 inline-flex items-center space-x-2 rounded-lg bg-white/10 px-4 lg:px-10 lg:px-10 py-3 backdrop-blur-sm">
          <Building class="h-5 w-5" />
          <span class="font-medium">{{ companies.length }} Perusahaan Mitra</span>
        </div>
      </div>
    </div>

    <div class="mx-auto max-w-7xl px-4 lg:px-10 py-8">
      <div class="mb-8 rounded-lg bg-white p-6 shadow-lg">
        <div class="flex flex-wrap items-center gap-4">
          <label class="font-medium text-gray-700">Filter Kategori:</label>
          <select
            v-model="selectedCategory"
            class="rounded-lg border border-gray-300 px-4 lg:px-10 py-2 focus:border-transparent focus:ring-2 focus:ring-purple-500"
          >
            <option value="all">Semua Kategori</option>
            <option v-for="cat in categories.slice(1)" :key="cat" :value="cat">
              {{ cat }}
            </option>
          </select>
          <span class="text-gray-600">{{ filteredCompanies.length }} perusahaan ditemukan</span>
        </div>
      </div>

      <div class="grid gap-6 md:grid-cols-2 lg:grid-cols-3">
        <article
          v-for="company in filteredCompanies"
          :key="company.id"
          class="cursor-pointer rounded-lg bg-white p-6 shadow-md transition-shadow hover:shadow-xl"
          @click="openDetail(company)"
        >
          <div class="mb-4 flex items-start justify-between">
            <div class="flex items-center space-x-3">
              <div
                class="flex h-12 w-12 items-center justify-center rounded-lg bg-gradient-to-br from-purple-500 to-indigo-500 text-xl font-bold text-white"
              >
                {{ company.name.charAt(0) }}
              </div>
              <div>
                <h3 class="text-lg font-semibold text-gray-900">{{ company.name }}</h3>
                <div class="flex items-center space-x-1 text-yellow-500">
                  <Star class="h-4 w-4 fill-current" />
                  <span class="text-sm font-medium">{{ company.rating }}</span>
                </div>
              </div>
            </div>
          </div>

          <p class="mb-4 line-clamp-3 text-sm text-gray-600">{{ company.description }}</p>

          <div class="mb-4 space-y-2">
            <div class="flex items-center space-x-2 text-sm text-gray-600">
              <MapPin class="h-4 w-4" />
              <span>{{ company.location }}</span>
            </div>
            <div class="flex items-center space-x-2 text-sm text-gray-600">
              <Briefcase class="h-4 w-4" />
              <span>{{ company.activeLowongan }} lowongan aktif</span>
            </div>
            <div class="flex items-center space-x-2 text-sm text-gray-600">
              <Users class="h-4 w-4" />
              <span>{{ company.totalInterns }} mahasiswa magang</span>
            </div>
          </div>

          <div class="flex items-center justify-between">
            <span class="rounded-full bg-purple-100 px-3 py-1 text-sm text-purple-700">
              {{ company.category }}
            </span>
            <button
              class="text-sm font-medium text-purple-600 hover:text-purple-700"
              @click.stop="openDetail(company)"
            >
              Lihat Detail ->
            </button>
          </div>
        </article>
      </div>
    </div>

    <div
      v-if="selectedCompany"
      class="fixed inset-0 z-[60] flex items-center justify-center overflow-y-auto bg-black/50 p-4"
    >
      <div class="my-8 w-full max-w-2xl rounded-lg bg-white">
        <div class="border-b border-gray-200 p-6">
          <div class="flex items-start justify-between">
            <div class="flex items-center space-x-4">
              <div
                class="flex h-16 w-16 items-center justify-center rounded-lg bg-gradient-to-br from-purple-500 to-indigo-500 text-2xl font-bold text-white"
              >
                {{ selectedCompany.name.charAt(0) }}
              </div>
              <div>
                <h2 class="text-2xl font-bold text-gray-900">{{ selectedCompany.name }}</h2>
                <div class="mt-1 flex items-center space-x-1 text-yellow-500">
                  <Star class="h-5 w-5 fill-current" />
                  <span class="font-medium">{{ selectedCompany.rating }}</span>
                  <span class="ml-2 text-sm text-gray-500">(Sejak {{ selectedCompany.established }})</span>
                </div>
              </div>
            </div>
            <button class="text-gray-400 transition-colors hover:text-gray-600" @click="closeDetail">
              <X class="h-6 w-6" />
            </button>
          </div>

          <span class="mt-4 inline-block rounded-full bg-purple-100 px-3 py-1 text-sm text-purple-700">
            {{ selectedCompany.category }}
          </span>
        </div>

        <div class="max-h-96 overflow-y-auto p-6">
          <div class="mb-6">
            <h3 class="mb-2 text-lg font-semibold text-gray-900">Tentang Perusahaan</h3>
            <p class="text-gray-700">{{ selectedCompany.description }}</p>
          </div>

          <div class="mb-6 grid gap-4 md:grid-cols-2">
            <div class="rounded-lg bg-blue-50 p-4">
              <div class="mb-2 flex items-center space-x-2 text-blue-600">
                <Briefcase class="h-5 w-5" />
                <span class="font-semibold">Lowongan Aktif</span>
              </div>
              <p class="text-2xl font-bold text-gray-900">{{ selectedCompany.activeLowongan }}</p>
            </div>

            <div class="rounded-lg bg-green-50 p-4">
              <div class="mb-2 flex items-center space-x-2 text-green-600">
                <Users class="h-5 w-5" />
                <span class="font-semibold">Total Mahasiswa Magang</span>
              </div>
              <p class="text-2xl font-bold text-gray-900">{{ selectedCompany.totalInterns }}</p>
            </div>
          </div>

          <div class="mb-6">
            <h3 class="mb-3 text-lg font-semibold text-gray-900">Informasi Kontak</h3>
            <div class="space-y-3">
              <div class="flex items-start space-x-3">
                <MapPin class="mt-0.5 h-5 w-5 text-gray-400" />
                <div>
                  <p class="text-sm text-gray-600">Alamat</p>
                  <p class="text-gray-900">{{ selectedCompany.address }}</p>
                </div>
              </div>

              <div class="flex items-start space-x-3">
                <Mail class="mt-0.5 h-5 w-5 text-gray-400" />
                <div>
                  <p class="text-sm text-gray-600">Email</p>
                  <a :href="`mailto:${selectedCompany.email}`" class="text-purple-600 hover:underline">
                    {{ selectedCompany.email }}
                  </a>
                </div>
              </div>

              <div class="flex items-start space-x-3">
                <Phone class="mt-0.5 h-5 w-5 text-gray-400" />
                <div>
                  <p class="text-sm text-gray-600">Telepon</p>
                  <a :href="`tel:${selectedCompany.phone}`" class="text-purple-600 hover:underline">
                    {{ selectedCompany.phone }}
                  </a>
                </div>
              </div>

              <div v-if="selectedCompany.website" class="flex items-start space-x-3">
                <Globe class="mt-0.5 h-5 w-5 text-gray-400" />
                <div>
                  <p class="text-sm text-gray-600">Website</p>
                  <a
                    :href="selectedCompany.website"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="text-purple-600 hover:underline"
                  >
                    {{ selectedCompany.website }}
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="flex gap-3 border-t border-gray-200 p-6">
          <button
            class="flex-1 rounded-lg border border-gray-300 px-6 py-3 transition-colors hover:bg-gray-50"
            @click="closeDetail"
          >
            Tutup
          </button>
          <button
            class="flex-1 rounded-lg bg-purple-600 px-6 py-3 font-medium text-white transition-colors hover:bg-purple-700"
            @click="props.onLoginClick"
          >
            Lihat Lowongan
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
