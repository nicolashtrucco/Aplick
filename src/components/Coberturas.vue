<script setup>
const coberturas = [
  {
    icon: 'bi-shield-check',
    title: 'Responsabilidad Civil',
    description: 'Cobertura obligatoria ante daños a terceros.',
    badge: 'Protección básica, simple y accesible.',
  },
  {
    icon: 'bi-car-front-fill',
    title: 'Terceros Completo',
    description: 'Incluye robo, incendio y daños parciales.',
    badge: 'Equilibrio ideal entre precio y protección.',
  },
  {
    icon: 'bi-shield-lock-fill',
    title: 'Todo Riesgo',
    description: 'Cobertura integral ante daños propios y a terceros.',
    badge: 'Máxima tranquilidad para tu vehículo.',
  },
]
</script>

<template>
  <section class="w-full py-4">
    <div class="w-full">
      <!-- Main Container with Radial Gradient -->
      <div 
        class="rounded-3xl overflow-hidden"
        style="
          background-image: url('/BgCoberturas.jpg');
          background-size: cover;
          background-position: center;
          background-repeat: no-repeat;
        "
      >
        <div class="px-6 sm:px-12 lg:px-16 py-16 sm:py-20">
          <!-- Header Section -->
          <div class="text-center mb-16">
            <p class="text-sm font-medium text-[#f7f7ad] uppercase tracking-widest mb-4">
              Coberturas
            </p>
            <h2 class="text-4xl sm:text-5xl lg:text-6xl font-black text-white leading-tight mb-6">
              Elige la cobertura<br>que se adapte a ti
            </h2>
            <p class="text-lg text-white/70 max-w-2xl mx-auto">
              Tres opciones de cobertura diseñadas para proteger tu vehículo según tus necesidades y presupuesto.
            </p>
          </div>

          <!-- Coverage Cards Grid -->
          <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
            <div v-for="(cobertura, index) in coberturas" :key="index" class="group flex flex-col items-center text-center">
              <!-- Icon -->
              <div class="w-12 h-12 rounded-full flex items-center justify-center mb-4 group-hover:scale-110 transition-transform duration-300" style="background: linear-gradient(135deg, #8fcf9a 0%, #195d4c 100%);">
                <i :class="['bi', cobertura.icon, 'text-white text-base']"></i>
              </div>

              <!-- Title -->
              <h3 class="text-sm font-bold text-white mb-2">
                {{ cobertura.title }}
              </h3>

              <!-- Description -->
              <p class="text-white/60 text-xs leading-relaxed">
                {{ cobertura.description }}
              </p>

              <!-- Badge -->
              <div 
  class="mt-4 inline-block px-3 py-1 rounded-full text-xs font-medium text-[#f7f7ad]" 
  style="background: rgba(247, 247, 173, 0.15); border: 1px solid rgba(247, 247, 173, 0.3);"
>
  {{ cobertura.badge }}
</div>
            </div>
          </div>

          <!-- CTA Button -->
          <div class="flex justify-center mt-12">
            <button class="px-8 py-4 bg-[#8fcf9a] text-[#195d4c] font-bold text-lg rounded-full hover:bg-[#f7f7ad] transition-all duration-300 shadow-lg hover:shadow-xl">
              Ver todas las coberturas
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
@import url('https://cdn.jsdelivr.net/npm/bootstrap-icons@1.13.1/font/bootstrap-icons.css');
</style>
