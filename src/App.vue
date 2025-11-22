<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import { Droplet } from 'lucide-vue-next';
import { Shield } from 'lucide-vue-next';
import { Wrench } from 'lucide-vue-next';
import { Droplets } from 'lucide-vue-next';
import { User } from 'lucide-vue-next';

const whatsappNumber = ref('6285719653175')
const phone = ref('+62-857-1965-3175')
const displayWhatsApp = ref('+62-857-1965-3175')
const officeAddress = ref('Jl. Contoh No.1, Kota Contoh')
const quickMessage = 'Halo, saya mau tanya layanan dan harga.'

const isOpen = ref(false)
const testimonials = ref([
  { name: 'Ahmad Mandau Soap', location: 'Bogor', message: 'Jam 14 an Istri saya lapor Air kran tidak keluar sama sama sekali, mesin semi jetpum mati.....saya cari di google maps tukang jasa toren terdekat dan diurutan teratas muncul alamat & no kontak Kang Budi & kang Dudi. Langsung saya telepon dan mereka menyanggupi datang . Respon cepat mereka datang dan mengerjakan penggantian flow switch.... Alhamdulillah Air bisa keluar lagi.... Mereka sangat berpengalaman dan menguasai betul proses perbaikan dan pengerjaan sirkulasi Air dan Mesin jetpum....harga jasa yang mereka tetapkan sangat bersahabat..dan ada garansi pengerjaan nya.... Semoga berkah dan dimurahkan rezekinya Kang Dudi & kang Budi.... Semogah semakin banyak Pelanggan.... Aamiin 3x YRA 🤲🤲🤲', avatar: User },
  { name: 'Wawan Nurdiawan', location: 'Bogor', message: 'Terimakasih bapak..... Ok service nya.... Sangat membantu pompa air saya lancar lagi.', avatar: User },
  { name: 'Widji purwanto', location: 'Bogor', message: 'Pengerjaan profesional dan tenaganya ahli. Mantab pokoknya dan jangan ragu soal pekerjaan', avatar: User },
  { name: 'Jems Cell', location: 'Bogor', message: 'Perbaikan sesuai kerusakan, no drama drama ini itu, hasilnya cukup memuaskan', avatar: User }
])
const activeIndex = ref(0)
let intervalId = null

onMounted(() => {
  intervalId = setInterval(() => {
    activeIndex.value = (activeIndex.value + 1) % testimonials.value.length
  }, 5000)
})

onBeforeUnmount(() => {
  if (intervalId) clearInterval(intervalId)
})

const maps = ref([
  { title: 'Cabang Utama', address: 'Kota A — Area service', mapEmbed: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d63417.809287572614!2d106.78047686953126!3d-6.570419995002769!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e69c169b48008a1%3A0xc1ccaeb255840f74!2sPerbaikan%20pompa%20air%20%2B%20cuci%20Toren!5e0!3m2!1sid!2sid!4v1763838246741!5m2!1sid!2sid' },
  { title: 'Gudang / Servis', address: 'Kota B — Area service', mapEmbed: 'https://www.google.com/maps/embed?pb=!1m17!1m12!1m3!1d3963.7144071455077!2d106.78218!3d-6.557690999999999!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m2!1m1!2zNsKwMzMnMjcuNyJTIDEwNsKwNDYnNTUuOSJF!5e0!3m2!1sid!2sid!4v1763838390103!5m2!1sid!2sid' },
  { title: 'Pusat Survei', address: 'Kota C — Area service', mapEmbed: 'https://www.google.com/maps/embed?pb=!1m17!1m12!1m3!1d3963.3820612736986!2d106.81919699999999!3d-6.599349999999999!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m2!1m1!2zNsKwMzUnNTcuNyJTIDEwNsKwNDknMDkuMSJF!5e0!3m2!1sid!2sid!4v1763838430671!5m2!1sid!2sid' }
])

function contactService(serviceName) {
  const text = `Halo, saya minta info layanan: ${serviceName}`
  const url = `https://wa.me/${whatsappNumber.value}?text=${encodeURIComponent(text)}`
  window.open(url, '_blank')
}
</script>

<template>
  <div class="min-h-screen flex flex-col font-sans text-gray-800 bg-white">
    <!-- Navbar -->
    <header class="fixed w-full z-40 bg-white/90 backdrop-blur-sm shadow-sm">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex justify-between items-center h-16">
          <div class="text-2xl font-bold text-blue-600">AquaCare</div>
          <nav class="hidden md:flex gap-6 text-gray-700">
            <a href="#services" class="hover:text-blue-600">Layanan</a>
            <a href="#testimonials" class="hover:text-blue-600">Testimoni</a>
            <a href="#locations" class="hover:text-blue-600">Lokasi</a>
            <a href="#contact" class="hover:text-blue-600">Kontak</a>
          </nav>
          <div class="hidden md:block">
            <a :href="`https://wa.me/${whatsappNumber}`" target="_blank"
              class="inline-flex items-center gap-2 px-4 py-2 bg-green-600 text-white rounded-md hover:bg-green-700">
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-whatsapp"
                viewBox="0 0 16 16">
                <path
                  d="M13.601 2.326A7.85 7.85 0 0 0 7.994 0C3.627 0 .068 3.558.064 7.926c0 1.399.366 2.76 1.057 3.965L0 16l4.204-1.102a7.9 7.9 0 0 0 3.79.965h.004c4.368 0 7.926-3.558 7.93-7.93A7.9 7.9 0 0 0 13.6 2.326zM7.994 14.521a6.6 6.6 0 0 1-3.356-.92l-.24-.144-2.494.654.666-2.433-.156-.251a6.56 6.56 0 0 1-1.007-3.505c0-3.626 2.957-6.584 6.591-6.584a6.56 6.56 0 0 1 4.66 1.931 6.56 6.56 0 0 1 1.928 4.66c-.004 3.639-2.961 6.592-6.592 6.592m3.615-4.934c-.197-.099-1.17-.578-1.353-.646-.182-.065-.315-.099-.445.099-.133.197-.513.646-.627.775-.114.133-.232.148-.43.05-.197-.1-.836-.308-1.592-.985-.59-.525-.985-1.175-1.103-1.372-.114-.198-.011-.304.088-.403.087-.088.197-.232.296-.346.1-.114.133-.198.198-.33.065-.134.034-.248-.015-.347-.05-.099-.445-1.076-.612-1.47-.16-.389-.323-.335-.445-.34-.114-.007-.247-.007-.38-.007a.73.73 0 0 0-.529.247c-.182.198-.691.677-.691 1.654s.71 1.916.81 2.049c.098.133 1.394 2.132 3.383 2.992.47.205.84.326 1.129.418.475.152.904.129 1.246.08.38-.058 1.171-.48 1.338-.943.164-.464.164-.86.114-.943-.049-.084-.182-.133-.38-.232" />
              </svg>
              WA
            </a>
          </div>
          <button @click="isOpen = !isOpen" class="md:hidden inline-flex items-center px-3 py-2 text-gray-700">
            <svg v-if="!isOpen" xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
              stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
            </svg>
            <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24"
              stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>
      </div>

      <div v-show="isOpen" class="md:hidden border-t border-gray-200 bg-white">
        <div class="px-4 py-3 flex flex-col gap-3">
          <a href="#services" @click="isOpen = false">Layanan</a>
          <a href="#testimonials" @click="isOpen = false">Testimoni</a>
          <a href="#locations" @click="isOpen = false">Lokasi</a>
          <a href="#contact" @click="isOpen = false">Kontak</a>
        </div>
      </div>
    </header>

    <main class="pt-20 flex-1">
      <!-- Hero -->
      <section class="bg-blue-50 py-20">
        <div class="max-w-5xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col lg:flex-row items-center gap-10">
          <div class="flex-1">
            <h1 class="text-4xl lg:text-5xl font-extrabold text-blue-700 mb-4">Service / Perbaikan Mesin Pompa air dan
              Cuci toren Bogor</h1>
            <p class="text-gray-600 text-lg mb-6">Deteksi kebocoran, cuci toren, perbaikan jet pump, filter air & sumur
              bor — harga transparan, teknisi berpengalaman.</p>
            <div class="flex gap-4">
              <a :href="`https://wa.me/${whatsappNumber}?text=${encodeURI(quickMessage)}`" target="_blank"
                class="px-6 py-3 rounded-md bg-green-600 text-white font-semibold hover:bg-green-700">Hubungi via WA</a>
              <a :href="``"
                class="px-6 py-3 rounded-md border border-blue-600 text-blue-600 hover:bg-blue-50">Telepon</a>
            </div>
          </div>
          <div class="flex-1 text-center p-2 gap-2 bg-white shadow-lg grid md:grid-cols-2 grid-cols-1 w-full">
            <!-- Bisa diterapkan gambar ilustrasi atau foto layanannya -->
            <div
              class="bg-linear-to-r hover:scale-105 transition duration-200 flex flex-col justify-center items-center from-sky-100 to-blue-100 rounded w-full h-35">
              <Droplet class="w-15 h-15 mb-1 bg-[#08c2ce] p-1 rounded-lg text-white" />
              <span class="text-md">Cuci Toren</span>
            </div>
            <div
              class="bg-linear-to-r hover:scale-105 transition duration-200 flex flex-col justify-center items-center from-sky-100 to-blue-100 rounded w-full h-35">
              <Shield class="w-15 h-15 mb-1 bg-[#08c2ce] p-1 rounded-lg text-white" />
              <span class="text-md">Filter Air</span>
            </div>
            <div
              class="bg-linear-to-r hover:scale-105 transition duration-200 flex flex-col justify-center items-center from-sky-100 to-blue-100 rounded w-full h-35">
              <Wrench class="w-15 h-15 mb-1 bg-[#08c2ce] p-1 rounded-lg text-white" />
              <span class="text-md">Perbaikan Mesin</span>
            </div>
            <div
              class="bg-linear-to-r hover:scale-105 transition duration-200 flex flex-col justify-center items-center from-sky-100 to-blue-100 rounded w-full h-35">
              <Droplets class="w-15 h-15 mb-1 bg-[#08c2ce] p-1 rounded-lg text-white" />
              <span class="text-md">Deteksi Kebocoran</span>
            </div>
          </div>
        </div>
      </section>

      <!-- Layanan -->
      <section id="services" class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-16">
        <h2 class="text-3xl font-bold mb-10 text-blue-700">Layanan Kami</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <!-- ulang untuk tiap layanan -->
          <div class="bg-white rounded-xl shadow-lg p-6 hover:shadow-xl transition-shadow">
            <h3 class="text-xl font-semibold mb-3">Deteksi Kebocoran</h3>
            <p class="text-gray-600 mb-4">Pendeteksian titik kebocoran menggunakan alat profesional. Biaya per titik Rp
              500.000.</p>
            <button @click="contactService('Deteksi Kebocoran')"
              class="mt-2 px-4 py-2 rounded-md bg-blue-400 text-white hover:bg-blue-500 cursor-pointer transition duration-200">Pesan
              Sekarang</button>
          </div>
          <div class="bg-white rounded-xl shadow-lg p-6 hover:shadow-xl transition-shadow">
            <h3 class="text-xl font-semibold mb-3">Cuci Toren</h3>
            <p class="text-gray-600 mb-4">Pembersihan toren & sanitasi.</p>
            <ul class="text-gray-700 mb-4">
              <li class="list-disc marker:text-blue-400">300 L — Rp 150.000</li>
              <li class="list-disc marker:text-blue-400">500 L — Rp 200.000</li>
              <li class="list-disc marker:text-blue-400">600/650 L — Rp 300.000</li>
              <li class="list-disc marker:text-blue-400">1.000 L — Rp 350.000</li>
            </ul>
            <button @click="contactService('Cuci Toren')"
              class="mt-2 px-4 py-2 rounded-md bg-blue-400 text-white hover:bg-blue-500 cursor-pointer transition duration-200">Pesan
              Sekarang</button>
          </div>
          <div class="bg-white rounded-xl shadow-lg p-6 hover:shadow-xl transition-shadow">
            <h3 class="text-xl font-semibold mb-3">Perbaikan Mesin pompa / Penggantian sparepart mesin</h3>
            <p class="text-gray-600 mb-4">Perbaikan, overhaul, atau penggantian sparepart. Estimasi di lokasi setelah
              pengecekan.</p>
            <button @click="contactService('Perbaikan Mesin / Jet Pump')"
              class="mt-2 px-4 py-2 rounded-md bg-blue-400 text-white hover:bg-blue-500 cursor-pointer transition duration-200">Minta
              Estimasi</button>
          </div>
          <div class="bg-white rounded-xl shadow-lg p-6 hover:shadow-xl transition-shadow">
            <h3 class="text-xl font-semibold mb-3">Filter Air</h3>
            <p class="text-gray-600 mb-4">Servis & instalasi sistem penyaringan air.</p>
            <ul class="text-gray-700 mb-4">
              <li class="list-disc marker:text-blue-400">Backwash filter — Rp 100.000</li>
              <li class="list-disc marker:text-blue-400">Ganti media filter — Rp 1.500.000</li>
              <li class="list-disc marker:text-blue-400">Instalasi filter — Rp 300.000</li>
              <li class="list-disc marker:text-blue-400">Paket lengkap (filter baru) — Rp 1.500.000</li>
            </ul>
            <button @click="contactService('Filter Air')"
              class="mt-2 px-4 py-2 rounded-md  bg-blue-400 text-white hover:bg-blue-500 cursor-pointer transition duration-200">Konsultasi
              Filter</button>
          </div>
          <div class="bg-white rounded-xl shadow-lg p-6 hover:shadow-xl transition-shadow col-span-1 md:col-span-2">
            <h3 class="text-xl font-semibold mb-3">Pembuatan Sumur Bor</h3>
            <p class="text-gray-600 mb-4">Pembuatan sumur bor untuk kebutuhan air bersih. Harga tergantung lokasi &
              kedalaman.</p>
            <button @click="contactService('Pembuatan Sumur Bor')"
              class="mt-2 px-4 py-2 rounded-md bg-blue-400 text-white hover:bg-blue-500 cursor-pointer transition duration-200">Minta
              Survey</button>
          </div>
        </div>
      </section>

      <!-- Testimoni -->
      <section id="testimonials" class="bg-blue-50 py-16">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 ">
          <h2 class="text-3xl font-bold mb-8 text-blue-700 text-center">Testimoni Pelanggan</h2>
          <div class="relative overflow-hidden rounded-xl">
            <div class="flex transition-transform duration-500"
              :style="{ transform: `translateX(-${activeIndex * 100}%)` }">
              <div v-for="(t, i) in testimonials" :key="i"
                class="min-w-full p-8 bg-white flex flex-col md:flex-row items-center gap-6">
                <span class="w-24 h-24 rounded-full border">
                  <component :is="t.avatar" alt="avatar" class="w-24 h-24 rounded-full object-cover" />
                </span>
                <div>
                  <h3 class="font-semibold text-xl">{{ t.name }}</h3>
                  <p class="text-sm text-gray-600 mb-2">{{ t.location }}</p>
                  <p class="text-gray-700">{{ t.message }}</p>
                </div>
              </div>
            </div>
            <div class="flex justify-center gap-2 mt-6">
              <button v-for="(_, i) in testimonials" :key="i" @click="activeIndex = i"
                :class="['w-3 h-3 rounded-full', activeIndex === i ? 'bg-blue-700' : 'bg-gray-300']"></button>
            </div>
          </div>
        </div>
      </section>

      <!-- Lokasi -->
      <section id="locations" class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-16">
        <h2 class="text-3xl font-bold mb-10 text-blue-700">Lokasi & Area Layanan</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div v-for="(m, idx) in maps" :key="idx" class="rounded-xl overflow-hidden shadow-lg">
            <div class="p-4 bg-white">
              <!-- <h3 class="font-semibold">{{ m.title }}</h3> -->
              <!-- <p class="text-sm text-gray-600 mb-3">{{ m.address }}</p> -->
            </div>
            <div class="w-full h-48 md:h-40">
              <iframe :src="m.mapEmbed" class="w-full h-full border-0" allowfullscreen loading="lazy"></iframe>
            </div>
          </div>
        </div>
      </section>

      <!-- Contact -->
      <section id="contact" class="bg-white py-16">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 grid grid-cols-1 md:grid-cols-3 gap-8 items-center">
          <div class="md:col-span-2">
            <h2 class="text-3xl font-bold mb-3 text-blue-700">Ingin Layanan Sekarang? Hubungi Kami</h2>
            <p class="text-gray-600 mb-4">Kirim pesan via WhatsApp atau telepon langsung. Sertakan alamat & jenis
              layanan agar kami bisa kirim estimasi cepat.</p>
            <div class="flex gap-4">
              <a :href="`https://wa.me/${whatsappNumber}`" target="_blank"
                class="px-6 py-3 rounded-md bg-green-600 text-white font-semibold hover:bg-green-700">WA: {{
                  displayWhatsApp }}</a>
              <a :href="`tel:${phone}`"
                class="px-6 py-3 rounded-md border border-blue-600 text-blue-600 hover:bg-blue-50">Telepon: {{ phone
                }}</a>
            </div>
          </div>

        </div>
      </section>
    </main>

    <footer class="bg-gray-100 border-t">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-6 flex flex-col md:flex-row justify-between items-center">
        <div class="text-sm text-gray-600">© {{ new Date().getFullYear() }} AquaCare — Semua hak dilindungi.</div>
        <div class="flex gap-4 mt-3 md:mt-0">
          <a :href="`https://wa.me/${whatsappNumber}`" target="_blank"
            class="text-gray-600 hover:text-blue-700">WhatsApp</a>
          <a :href="`tel:${phone}`" class="text-gray-600 hover:text-blue-700">Telepon</a>
        </div>
      </div>
    </footer>
  </div>
</template>

<style scoped>
/* Tambahan style jika perlu */
</style>
