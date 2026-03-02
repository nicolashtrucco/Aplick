<script setup>
const steps = [
  {
    number: 1,
    title: 'Abre WhatsApp',
    description: 'Inicia una conversación con nuestro asistente IA de forma inmediata y sin complicaciones.',
  },
  {
    number: 2,
    title: 'Responde preguntas',
    description: 'El chatbot inteligente te guía a través de un cuestionario simple y rápido sobre tu vehículo.',
  },
  {
    number: 3,
    title: 'Recibe cotización',
    description: 'Obtén en segundos múltiples opciones de cobertura con precios accesibles y transparentes.',
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
          background-image: url('../../public/BgHowItWorks.png');
          background-size: cover;
          background-position: center;
          background-repeat: no-repeat;
        "
      >
        <div class="px-6 sm:px-12 lg:px-16 py-16 sm:py-20">
          <!-- Header Section -->
          <div class="text-center mb-16">
            <p class="text-sm font-medium text-[#f7f7ad] uppercase tracking-widest mb-4">
              Cómo funciona
            </p>
            <h2 class="text-4xl sm:text-5xl lg:text-6xl font-black text-white leading-tight mb-6">
              Cotiza tu seguro<br>en 3 pasos simples
            </h2>
            <p class="text-lg text-white/70 max-w-2xl mx-auto">
              Utiliza nuestro asistente IA integrado en WhatsApp para obtener las mejores opciones de cobertura de forma simple, rápida y accesible.
            </p>
          </div>

          <!-- Steps Grid -->
          <div class="grid grid-cols-1 md:grid-cols-3 gap-8 mt-16">
            <div v-for="step in steps" :key="step.number" class="relative">
              <!-- Step Number Circle -->
              <div class="flex items-center justify-center w-16 h-16 rounded-full mx-auto mb-6" style="background: linear-gradient(135deg, #8fcf9a 0%, #195d4c 100%);">
                <span class="text-2xl font-black text-white">{{ step.number }}</span>
              </div>

              <!-- Step Content -->
              <div class="text-center">
                <h3 class="text-xl font-bold text-white mb-3">
                  {{ step.title }}
                </h3>
                <p class="text-white/60 text-sm leading-relaxed">
                  {{ step.description }}
                </p>
              </div>

              <!-- Connector Line (hidden on mobile) -->
              <div v-if="step.number < 3" class="hidden md:block absolute top-8 left-[calc(50%+2rem)] w-[calc(100%-4rem)] h-1 bg-gradient-to-r from-[#8fcf9a] via-[#195d4c] to-transparent"></div>
            </div>
          </div>

          <!-- CTA Button -->
          <div class="flex justify-center mt-16">
            <button class="px-8 py-4 bg-[#8fcf9a] text-[#195d4c] font-bold text-lg rounded-full hover:bg-[#f7f7ad] transition-all duration-300 shadow-lg hover:shadow-xl">
              Comenzar ahora
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
</style>
