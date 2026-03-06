<script setup>
import { ref } from 'vue'
import MarqueeVertical from './MarqueeVertical.vue'
import ReasonCard from './ReasonCard.vue'

const reasons = [
  {
    icon: 'bi-rocket-takeoff-fill',
    title: 'Velocidad',
    description: 'Cotiza en segundos, sin esperas ni trámites innecesarios.',
  },
  {
    icon: 'bi-check-circle-fill',
    title: 'Transparencia',
    description: 'Sin sorpresas. Ves exactamente qué cubre tu seguro desde el inicio.',
  },
  {
    icon: 'bi-wallet2',
    title: 'Mejores Precios',
    description: 'Comparamos opciones para encontrar la mejor relación precio-cobertura.',
  },
  {
    icon: 'bi-headset',
    title: 'Soporte 24/7',
    description: 'Nuestro asistente IA está siempre disponible en WhatsApp.',
  },
  {
    icon: 'bi-shield-lock-fill',
    title: 'Seguridad',
    description: 'Tus datos están protegidos con los más altos estándares de cifrado.',
  },
  {
    icon: 'bi-phone-fill',
    title: 'Accesible',
    description: 'Desde cualquier dispositivo, en cualquier momento, en cualquier lugar.',
  },
]
</script>

<template>
  <section 
    class="w-full py-16 sm:py-20 relative"
    style="
      background-image: url('/BgPorqueElegirnos.jpg');
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
    "
  >
    <!-- Top fade from black -->
    <div class="absolute top-0 left-0 right-0 h-92 bg-gradient-to-b from-black to-transparent pointer-events-none z-10"></div>

    <!-- Bottom fade to black -->
    <div class="absolute bottom-0 left-0 right-0 h-32 bg-gradient-to-t from-black to-transparent pointer-events-none z-10"></div>

    <div class="w-full px-6 sm:px-12 lg:px-16 relative z-20">
      <!-- Two Column Layout -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 lg:gap-16 items-start">
        
        <!-- Left Column: Text Content -->
        <div class="flex flex-col justify-center">
          <p class="text-sm font-medium text-[#f7f7ad] uppercase tracking-widest mb-4">
            Ventajas
          </p>
          <h2 class="text-4xl sm:text-5xl lg:text-6xl font-black text-white leading-tight mb-6">
            Por qué elegirnos
          </h2>
          <p class="text-lg text-white/70 leading-relaxed">
            Somos más que una plataforma de cotización. Somos tu aliado en la búsqueda del mejor seguro vehicular, con tecnología inteligente y atención personalizada.
          </p>
        </div>

        <!-- Right Column: Vertical Carousel -->
        <div class="relative overflow-hidden rounded-2xl h-80" style="mask-image: linear-gradient(to bottom, transparent 0%, black 20%, black 80%, transparent 100%); -webkit-mask-image: linear-gradient(to bottom, transparent 0%, black 20%, black 80%, transparent 100%);">
          <MarqueeVertical
            :pause-on-hover="true"
            class="[--duration:30s]"
          >
            <ReasonCard
              v-for="reason in reasons"
              :key="reason.title"
              :icon="reason.icon"
              :title="reason.title"
              :description="reason.description"
            />
          </MarqueeVertical>
        </div>

      </div>
    </div>
  </section>
</template>

<style scoped>
@import url('https://cdn.jsdelivr.net/npm/bootstrap-icons@1.13.1/font/bootstrap-icons.css');
</style>
