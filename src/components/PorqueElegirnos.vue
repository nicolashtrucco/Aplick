<script setup>
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
  <section class="w-full py-4 pb-0">
    <div class="w-full">
      <!-- Main Container with Radial Gradient -->
      <div 
        class="rounded-3xl overflow-hidden"
        style="
          background-image: url('../../public/BgPorqueElegirnos.jpg');
          background-size: cover;
          background-position: center;
          background-repeat: no-repeat;
        "
      >
        <div class="px-6 sm:px-12 lg:px-16 py-16 sm:py-20">
          <!-- Header Section -->
          <div class="max-w-3xl mx-auto text-center mb-16">
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

          <!-- Reasons Grid - 3 Columns -->
          <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            <div v-for="(reason, index) in reasons" :key="index" class="group flex flex-col items-center text-center">
              <!-- Icon -->
              <div class="w-12 h-12 rounded-full flex items-center justify-center mb-4 group-hover:scale-110 transition-transform duration-300" style="background: linear-gradient(135deg, #8fcf9a 0%, #195d4c 100%);">
                <i :class="['bi', reason.icon, 'text-white text-base']"></i>
              </div>

              <!-- Content -->
              <h3 class="text-sm font-bold text-white mb-2">
                {{ reason.title }}
              </h3>
              <p class="text-white/60 text-xs leading-relaxed">
                {{ reason.description }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
@import url('https://cdn.jsdelivr.net/npm/bootstrap-icons@1.13.1/font/bootstrap-icons.css');
</style>
