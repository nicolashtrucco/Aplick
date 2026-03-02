<script setup>
const features = [
  {
    icon: 'bi-lightning-fill',
    title: 'Simple y Rápido',
    description: 'Cotiza tu seguro en segundos sin formularios complejos. Tecnología IA que entiende tus necesidades.',
  },
  {
    icon: 'bi-shield-check',
    title: 'Accesible y Confiable',
    description: 'Seguros verificados y regulados. Protección real con transparencia total en cada paso.',
  },
  {
    icon: 'bi-chat-dots-fill',
    title: 'Asistente IA 24/7',
    description: 'Nuestro chatbot inteligente en WhatsApp responde tus preguntas cuando las necesitas.',
  },
  {
    icon: 'bi-percent',
    title: 'Mejores Precios',
    description: 'Comparamos opciones para traerte las mejores coberturas al mejor precio del mercado.',
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
          background-image: url('../../public/BgAboutAplick.webp');
          background-size: cover;
          background-position: center;
          background-repeat: no-repeat;
        "
      >
        <div class="px-6 sm:px-12 lg:px-16 py-16 sm:py-20">
          <!-- Header Section -->
          <div class="max-w-3xl mb-16">
            <p class="text-sm font-medium text-[#f7f7ad] uppercase tracking-widest mb-4">
              Sobre Aplick
            </p>
            <h2 class="text-4xl sm:text-5xl font-black text-white leading-tight mb-6">
              La tecnología que simplifica los seguros
            </h2>
            <p class="text-lg text-white/70 leading-relaxed">
              APLICK es una plataforma digital que transforma la experiencia de cotizar seguros. Utilizamos inteligencia artificial integrada en WhatsApp para eliminar la complejidad tradicional del mundo de los seguros. Nuestro objetivo es convertir una tarea tediosa en algo simple, rápido y accesible para todos.
            </p>
          </div>

          <!-- Features Grid - Below Content -->
          <div class="grid grid-cols-2 md:grid-cols-4 gap-6">
            <div v-for="(feature, index) in features" :key="index" class="group flex flex-col items-center text-center">
              <!-- Icon -->
              <div class="w-12 h-12 rounded-full flex items-center justify-center mb-4 group-hover:scale-110 transition-transform duration-300" style="background: linear-gradient(135deg, #8fcf9a 0%, #195d4c 100%);">
                <i :class="['bi', feature.icon, 'text-white text-base']"></i>
              </div>

              <!-- Text -->
              <h3 class="text-sm font-bold text-white mb-2">
                {{ feature.title }}
              </h3>
              <p class="text-white/60 text-xs leading-relaxed">
                {{ feature.description }}
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
