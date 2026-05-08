<script setup>
import { computed, ref } from "vue";
import {
  Search,
  Filter,
  MapPin,
  Building,
  Calendar,
  Briefcase,
  ChevronRight,
  X,
} from "lucide-vue-next";

const props = defineProps({
  onLoginClick: {
    type: Function,
    default: () => {},
  },
});

const searchQuery = ref("");
const selectedCategory = ref("all");
const selectedLocation = ref("all");
const selectedLowongan = ref(null);

const lowongan = [
  {
    id: "1",
    title: "Web Developer Intern",
    company: "PT. Tech Indonesia",
    location: "Yogyakarta",
    type: "Full Time",
    category: "Technology",
    salary: "Rp 2.000.000 - 3.000.000",
    description:
      "Kami mencari mahasiswa berbakat untuk bergabung sebagai Web Developer Intern. Anda akan bekerja dengan tim developer profesional dalam mengembangkan aplikasi web modern.",
    requirements: [
      "Mahasiswa aktif minimal semester 5",
      "IPK minimal 3.0",
      "Menguasai HTML, CSS, JavaScript",
      "Familiar dengan React atau Vue.js",
      "Memahami konsep REST API",
      "Mampu bekerja dalam tim",
    ],
    responsibilities: [
      "Mengembangkan fitur aplikasi web",
      "Melakukan testing dan debugging",
      "Berkolaborasi dengan tim design dan backend",
      "Membuat dokumentasi teknis",
    ],
    postedDate: "2026-04-15",
    deadline: "2026-06-15",
    applicants: 24,
  },
  {
    id: "2",
    title: "Mobile App Developer Intern",
    company: "PT. Digital Solution",
    location: "Jakarta",
    type: "Full Time",
    category: "Technology",
    salary: "Rp 2.500.000 - 3.500.000",
    description:
      "Kesempatan bergabung dalam tim mobile development untuk mengembangkan aplikasi Android dan iOS menggunakan Flutter atau React Native.",
    requirements: [
      "Mahasiswa aktif minimal semester 6",
      "IPK minimal 3.0",
      "Menguasai Flutter atau React Native",
      "Pemahaman tentang mobile UI/UX",
      "Pengalaman dengan Git",
    ],
    responsibilities: [
      "Develop aplikasi mobile",
      "Implementasi design ke kode",
      "Integrasi dengan backend API",
      "Testing dan optimization",
    ],
    postedDate: "2026-04-20",
    deadline: "2026-06-20",
    applicants: 18,
  },
  {
    id: "3",
    title: "UI/UX Designer Intern",
    company: "Creative Studio",
    location: "Bandung",
    type: "Full Time",
    category: "Design",
    salary: "Rp 1.800.000 - 2.500.000",
    description:
      "Bergabunglah dengan tim creative untuk mendesain interface aplikasi dan website yang menarik dan user-friendly.",
    requirements: [
      "Mahasiswa DKV, Informatika, atau terkait",
      "Menguasai Figma dan Adobe XD",
      "Portfolio design yang menarik",
      "Pemahaman design thinking",
      "Komunikatif dan kreatif",
    ],
    responsibilities: [
      "Membuat wireframe dan mockup",
      "Design interface aplikasi/website",
      "Conduct user research",
      "Berkolaborasi dengan developer",
    ],
    postedDate: "2026-04-25",
    deadline: "2026-06-25",
    applicants: 31,
  },
  {
    id: "4",
    title: "Data Analyst Intern",
    company: "PT. Data Insights",
    location: "Yogyakarta",
    type: "Full Time",
    category: "Data Science",
    salary: "Rp 2.200.000 - 3.000.000",
    description:
      "Bantu tim data dalam menganalisis dan memvisualisasikan data untuk mendukung keputusan bisnis.",
    requirements: [
      "Mahasiswa Statistika, Informatika, atau terkait",
      "IPK minimal 3.2",
      "Menguasai Python atau R",
      "Familiar dengan SQL",
      "Pengalaman dengan tools visualisasi data",
    ],
    responsibilities: [
      "Analisis data menggunakan Python/R",
      "Membuat dashboard visualisasi",
      "Melakukan data cleaning",
      "Presentasi insight kepada stakeholder",
    ],
    postedDate: "2026-05-01",
    deadline: "2026-07-01",
    applicants: 15,
  },
  {
    id: "5",
    title: "Digital Marketing Intern",
    company: "PT. Marketing Hub",
    location: "Jakarta",
    type: "Full Time",
    category: "Marketing",
    salary: "Rp 1.500.000 - 2.000.000",
    description:
      "Pelajari strategi digital marketing dari praktisi berpengalaman dan bantu jalankan campaign marketing.",
    requirements: [
      "Mahasiswa Komunikasi, Marketing, atau terkait",
      "Kreatif dan update dengan tren digital",
      "Familiar dengan social media",
      "Kemampuan copywriting",
    ],
    responsibilities: [
      "Membuat konten social media",
      "Mengelola campaign digital",
      "Analisis performa marketing",
      "Email marketing",
    ],
    postedDate: "2026-05-03",
    deadline: "2026-07-03",
    applicants: 42,
  },
  {
    id: "6",
    title: "Backend Developer Intern",
    company: "PT. Tech Indonesia",
    location: "Yogyakarta",
    type: "Full Time",
    category: "Technology",
    salary: "Rp 2.300.000 - 3.200.000",
    description:
      "Kesempatan untuk belajar dan berkontribusi dalam pengembangan sistem backend yang scalable dan robust.",
    requirements: [
      "Mahasiswa Informatika minimal semester 5",
      "IPK minimal 3.0",
      "Menguasai Node.js atau Python/Django",
      "Pemahaman database SQL/NoSQL",
      "Familiar dengan REST API",
    ],
    responsibilities: [
      "Develop REST API",
      "Database design dan optimization",
      "Integration dengan third-party services",
      "Code review dan testing",
    ],
    postedDate: "2026-05-05",
    deadline: "2026-07-05",
    applicants: 20,
  },
];

const categories = ["all", "Technology", "Design", "Data Science", "Marketing"];
const locations = ["all", "Yogyakarta", "Jakarta", "Bandung", "Semarang"];

const filteredLowongan = computed(() => {
  return lowongan.filter((item) => {
    const keyword = searchQuery.value.toLowerCase();
    const matchSearch =
      item.title.toLowerCase().includes(keyword) ||
      item.company.toLowerCase().includes(keyword) ||
      item.description.toLowerCase().includes(keyword);
    const matchCategory =
      selectedCategory.value === "all" ||
      item.category === selectedCategory.value;
    const matchLocation =
      selectedLocation.value === "all" ||
      item.location === selectedLocation.value;

    return matchSearch && matchCategory && matchLocation;
  });
});

const formatDate = (dateText) => {
  return new Date(dateText).toLocaleDateString("id-ID");
};

const closeDetail = () => {
  selectedLowongan.value = null;
};

const openDetail = (item) => {
  selectedLowongan.value = item;
};
</script>

<template>
  <div class="min-h-screen bg-gray-50">
    <div class="bg-[#008BFF] pt-36 py-12 text-white">
      <div class="mx-auto max-w-7xl px-4 lg:px-10 text-center md:text-left">
        <h1 class="mb-4 text-4xl font-bold">Lowongan Magang</h1>

        <p class="text-xl opacity-90">
          Temukan pengalaman magang terbaik untuk karirmu
        </p>

        <div
          class="mt-6 inline-flex items-center space-x-2 rounded-lg bg-white/10 px-4 lg:px-10 py-3 backdrop-blur-sm md:mx-0 mx-auto"
        >
          <Briefcase class="h-5 w-5" />

          <span class="font-medium">
            {{ lowongan.length }} Lowongan Tersedia
          </span>
        </div>
      </div>
    </div>

    <div class="mx-auto max-w-7xl px-4 lg:px-10 py-8">
      <div class="mb-8 rounded-lg bg-white p-6 shadow-lg">
        <div class="grid gap-4 md:grid-cols-3">
          <div class="md:col-span-3">
            <div class="relative">
              <Search
                class="absolute left-4 top-1/2 h-5 w-5 -translate-y-1/2 text-gray-400"
              />
              <input
                v-model="searchQuery"
                type="text"
                placeholder="Cari berdasarkan posisi, perusahaan, atau kata kunci..."
                class="w-full rounded-lg border border-gray-300 py-3 pl-12 pr-4 focus:border-transparent focus:ring-2 focus:ring-blue-500"
              />
            </div>
          </div>

          <div>
            <select
              v-model="selectedCategory"
              class="w-full rounded-lg border border-gray-300 px-4 py-3 focus:border-transparent focus:ring-2 focus:ring-blue-500"
            >
              <option value="all">Semua Kategori</option>
              <option
                v-for="cat in categories.slice(1)"
                :key="cat"
                :value="cat"
              >
                {{ cat }}
              </option>
            </select>
          </div>

          <div>
            <select
              v-model="selectedLocation"
              class="w-full rounded-lg border border-gray-300 px-4 py-3 focus:border-transparent focus:ring-2 focus:ring-blue-500"
            >
              <option value="all">Semua Lokasi</option>
              <option v-for="loc in locations.slice(1)" :key="loc" :value="loc">
                {{ loc }}
              </option>
            </select>
          </div>

          <div class="flex items-center space-x-2">
            <Filter class="h-5 w-5 text-gray-500" />
            <span class="font-medium text-gray-700"
              >{{ filteredLowongan.length }} hasil ditemukan</span
            >
          </div>
        </div>
      </div>

      <div class="grid gap-6 md:grid-cols-2 lg:grid-cols-3">
        <article
          v-for="item in filteredLowongan"
          :key="item.id"
          class="cursor-pointer rounded-lg bg-white p-6 shadow-md transition-shadow hover:shadow-xl"
          @click="openDetail(item)"
        >
          <div class="mb-3 flex items-start justify-between">
            <div class="flex-1">
              <h3 class="mb-1 text-lg font-semibold text-gray-900">
                {{ item.title }}
              </h3>
              <div class="flex items-center space-x-1 text-gray-600">
                <Building class="h-4 w-4" />
                <span class="text-sm">{{ item.company }}</span>
              </div>
            </div>
          </div>

          <div class="mb-4 space-y-2">
            <div class="flex items-center space-x-2 text-sm text-gray-600">
              <MapPin class="h-4 w-4" />
              <span>{{ item.location }}</span>
            </div>
            <div class="flex items-center space-x-2 text-sm text-gray-600">
              <Calendar class="h-4 w-4" />
              <span>Deadline: {{ formatDate(item.deadline) }}</span>
            </div>
            <div v-if="item.salary" class="text-sm font-medium text-green-600">
              {{ item.salary }}
            </div>
          </div>

          <div class="flex items-center justify-between">
            <span
              class="rounded-full bg-blue-100 px-3 py-1 text-sm text-blue-700"
              >{{ item.category }}</span
            >
            <div class="flex items-center space-x-1 text-sm text-gray-500">
              <span>{{ item.applicants }} pelamar</span>
            </div>
          </div>

          <button
            class="mt-4 flex w-full items-center justify-center space-x-2 rounded-lg bg-blue-600 px-4 py-2 text-white transition-colors hover:bg-blue-700"
            @click.stop="openDetail(item)"
          >
            <span>Lihat Detail</span>
            <ChevronRight class="h-4 w-4" />
          </button>
        </article>
      </div>

      <div v-if="filteredLowongan.length === 0" class="py-12 text-center">
        <Briefcase class="mx-auto mb-4 h-16 w-16 text-gray-400" />
        <h3 class="mb-2 text-xl font-semibold text-gray-900">
          Tidak ada lowongan ditemukan
        </h3>
        <p class="text-gray-600">Coba ubah filter atau kata kunci pencarian</p>
      </div>
    </div>

    <div
      v-if="selectedLowongan"
      class="fixed inset-0 z-[60] flex items-center justify-center overflow-y-auto bg-black/50 p-4"
    >
      <div class="my-8 w-full max-w-3xl rounded-lg bg-white">
        <div class="border-b border-gray-200 p-6">
          <div class="mb-4 flex items-start justify-between">
            <div>
              <h2 class="mb-2 text-2xl font-bold text-gray-900">
                {{ selectedLowongan.title }}
              </h2>
              <div class="flex items-center space-x-4 text-gray-600">
                <div class="flex items-center space-x-1">
                  <Building class="h-4 w-4" />
                  <span>{{ selectedLowongan.company }}</span>
                </div>
                <div class="flex items-center space-x-1">
                  <MapPin class="h-4 w-4" />
                  <span>{{ selectedLowongan.location }}</span>
                </div>
              </div>
            </div>
            <button
              class="text-gray-400 transition-colors hover:text-gray-600"
              @click="closeDetail"
            >
              <X class="h-6 w-6" />
            </button>
          </div>

          <div class="flex flex-wrap gap-3">
            <span
              class="rounded-full bg-blue-100 px-3 py-1 text-sm text-blue-700"
            >
              {{ selectedLowongan.category }}
            </span>
            <span
              class="rounded-full bg-green-100 px-3 py-1 text-sm text-green-700"
            >
              {{ selectedLowongan.type }}
            </span>
            <span
              v-if="selectedLowongan.salary"
              class="rounded-full bg-purple-100 px-3 py-1 text-sm text-purple-700"
            >
              {{ selectedLowongan.salary }}
            </span>
          </div>
        </div>

        <div class="max-h-96 overflow-y-auto p-6">
          <div class="mb-6">
            <h3 class="mb-2 text-lg font-semibold text-gray-900">Deskripsi</h3>
            <p class="text-gray-700">{{ selectedLowongan.description }}</p>
          </div>

          <div class="mb-6">
            <h3 class="mb-2 text-lg font-semibold text-gray-900">
              Persyaratan
            </h3>
            <ul class="space-y-2">
              <li
                v-for="(req, idx) in selectedLowongan.requirements"
                :key="`${selectedLowongan.id}-req-${idx}`"
                class="flex items-start space-x-2"
              >
                <span class="mt-1 text-blue-600">•</span>
                <span class="text-gray-700">{{ req }}</span>
              </li>
            </ul>
          </div>

          <div class="mb-6">
            <h3 class="mb-2 text-lg font-semibold text-gray-900">
              Tanggung Jawab
            </h3>
            <ul class="space-y-2">
              <li
                v-for="(resp, idx) in selectedLowongan.responsibilities"
                :key="`${selectedLowongan.id}-resp-${idx}`"
                class="flex items-start space-x-2"
              >
                <span class="mt-1 text-blue-600">•</span>
                <span class="text-gray-700">{{ resp }}</span>
              </li>
            </ul>
          </div>

          <div class="grid gap-4 rounded-lg bg-gray-50 p-4 md:grid-cols-2">
            <div>
              <p class="text-sm text-gray-600">Tanggal Posting</p>
              <p class="font-medium text-gray-900">
                {{ formatDate(selectedLowongan.postedDate) }}
              </p>
            </div>
            <div>
              <p class="text-sm text-gray-600">Deadline</p>
              <p class="font-medium text-red-600">
                {{ formatDate(selectedLowongan.deadline) }}
              </p>
            </div>
            <div>
              <p class="text-sm text-gray-600">Jumlah Pelamar</p>
              <p class="font-medium text-gray-900">
                {{ selectedLowongan.applicants }} orang
              </p>
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
            class="flex-1 rounded-lg bg-blue-600 px-6 py-3 font-medium text-white transition-colors hover:bg-blue-700"
            @click="props.onLoginClick"
          >
            Daftar Sekarang
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
