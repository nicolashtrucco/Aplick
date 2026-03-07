<script setup>
import MarqueeVertical from './MarqueeVertical.vue'

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
      <!-- Two Column Layout - Centered -->
      <div class="flex flex-col lg:flex-row items-center justify-center gap-12 lg:gap-20 max-w-6xl mx-auto">
        
        <!-- Left Column: Text Content -->
        <div class="flex-1 flex flex-col justify-center">
          <p class="text-sm font-medium text-[#f7f7ad] uppercase tracking-widest mb-4">
            Ventajas
          </p>
          <h2 class="text-4xl sm:text-5xl font-black text-white leading-tight mb-6 whitespace-nowrap">
            Por qué <span style="color: #8fcf9a;">elegirnos</span>
          </h2>
          <p class="text-lg text-white/70 leading-relaxed max-w-sm">
            Somos tu aliado en la búsqueda del mejor seguro vehicular con tecnología inteligente y atención personalizada.
          </p>
        </div>

        <!-- Right Column: Vertical Carousel -->
        <div class="flex-1 w-full lg:w-auto flex items-center justify-center">
          <div class="relative overflow-hidden rounded-2xl h-80" style="mask-image: linear-gradient(to bottom, transparent 0%, black 20%, black 80%, transparent 100%); -webkit-mask-image: linear-gradient(to bottom, transparent 0%, black 20%, black 80%, transparent 100%);">
            <MarqueeVertical
              :pause-on-hover="true"
              :repeat="8"
              class="[--duration:120s] w-full"
            >
              <div v-for="reason in reasons" :key="reason.title" class="group relative rounded-2xl p-6 transition-all duration-300 backdrop-blur-xl overflow-visible mx-2 flex-shrink-0" style="background: rgba(255, 255, 255, 0.05); border: 1px solid rgba(255, 255, 255, 0.1); width: 500px; height: fit-content;">
                
                <!-- Icon Circle (Sobresale arriba) -->
                <div class="absolute -top-6 left-6 flex items-center justify-center w-12 h-12 rounded-full text-xl z-20" style="background: linear-gradient(135deg, #8fcf9a 0%, #195d4c 100%);">
                  <i :class="`bi ${reason.icon} text-white`"></i>
                </div>

                <!-- Content -->
                <div class="pt-4 w-full">
                  <h3 class="text-lg font-bold mb-2" style="color: #8fcf9a;">
                    {{ reason.title }}
                  </h3>
                  <p class="text-white/60 text-sm leading-relaxed">
                    {{ reason.description }}
                  </p>
                </div>
              </div>
            </MarqueeVertical>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>

<style scoped>
@import url('https://cdn.jsdelivr.net/npm/bootstrap-icons@1.13.1/font/bootstrap-icons.css');
</style>
