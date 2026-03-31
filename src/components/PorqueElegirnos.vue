<script setup lang="ts">
import MarqueeVertical from './MarqueeVertical.vue'
import gsap from 'gsap'
import { onMounted } from 'vue'

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

onMounted(() => {
  setTimeout(() => {
    animateTextContent()
  }, 100)
})

const animateTextContent = () => {
  // Animate label
  gsap.from('.ventajas-label', {
    opacity: 0,
    y: 20,
    duration: 0.6,
    ease: 'power2.out',
  })

  // Animate title
  gsap.from('.ventajas-title', {
    opacity: 0,
    y: 30,
    duration: 0.8,
    delay: 0.1,
    ease: 'power2.out',
  })

  // Animate description
  gsap.from('.ventajas-description', {
    opacity: 0,
    y: 20,
    duration: 0.7,
    delay: 0.2,
    ease: 'power2.out',
  })
}

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
          <p class="ventajas-label text-sm font-medium text-[#f7f7ad] uppercase tracking-widest mb-4">
            Ventajas
          </p>
          <h2 class="ventajas-title text-4xl sm:text-5xl font-black text-white leading-tight mb-6 whitespace-nowrap">
            Por qué <span style="color: #8fcf9a;">elegirnos</span>
          </h2>
          <p class="ventajas-description text-lg text-white/70 leading-relaxed max-w-sm">
            Somos tu aliado en la búsqueda del mejor seguro vehicular con tecnología inteligente y atención personalizada.
          </p>
        </div>

        <!-- Right Column: Vertical Carousel -->
        <div class="flex-1 w-full lg:w-auto flex items-center justify-center px-2 lg:px-0">
          <div class="relative overflow-hidden rounded-2xl h-80 w-full lg:w-auto max-w-xs lg:max-w-none" style="mask-image: linear-gradient(to bottom, transparent 0%, black 20%, black 80%, transparent 100%); -webkit-mask-image: linear-gradient(to bottom, transparent 0%, black 20%, black 80%, transparent 100%);">
            <MarqueeVertical
              :pause-on-hover="true"
              :repeat="8"
              :mobile-optimized="true"
              class="[--duration:120s] w-full"
            >
              <div v-for="reason in reasons" :key="reason.title" class="reason-card group relative rounded-2xl transition-all duration-300 backdrop-blur-xl overflow-visible flex-shrink-0" style="background: rgba(255, 255, 255, 0.05); border: 1px solid rgba(255, 255, 255, 0.1);">
                
                <!-- Icon Circle (Sobresale arriba) -->
                <div class="icon-circle absolute flex items-center justify-center rounded-full z-20" style="background: linear-gradient(135deg, #8fcf9a 0%, #195d4c 100%);">
                  <i :class="`bi ${reason.icon} text-white`"></i>
                </div>

                <!-- Content -->
                <div class="card-content">
                  <h3 class="card-title font-bold" style="color: #8fcf9a;">
                    {{ reason.title }}
                  </h3>
                  <p class="card-description text-white/60 leading-relaxed">
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

@media (max-width: 1023px) {
  .reason-card {
    width: 100% !important;
    max-width: 400px !important;
    padding: 16px !important;
    margin: 4px auto !important;
  }

  .reason-card .icon-circle {
    width: 40px;
    height: 40px;
    top: -16px;
    left: 16px;
    font-size: 16px;
  }

  .reason-card .card-title {
    font-size: 14px;
    margin-bottom: 4px;
  }

  .reason-card .card-description {
    font-size: 12px;
  }

  .reason-card .card-content {
    padding-top: 12px;
  }
}

@media (min-width: 1024px) {
  .reason-card {
    width: 500px !important;
    padding: 24px !important;
    margin: 8px !important;
  }

  .reason-card .icon-circle {
    width: 48px;
    height: 48px;
    top: -24px;
    left: 24px;
    font-size: 20px;
  }

  .reason-card .card-title {
    font-size: 18px;
    margin-bottom: 8px;
  }

  .reason-card .card-description {
    font-size: 14px;
  }

  .reason-card .card-content {
    padding-top: 16px;
  }
}
</style>
