<script setup>
const steps = [
  {
    number: 1,
    title: 'Escribinos',
    description: 'Iniciá una conversación con nuestro asistente IA.',
  },
  {
    number: 2,
    title: 'Respondé las preguntas',
    description: 'Cuestionario simple sobre tu seguro.',
  },
  {
    number: 3,
    title: 'Recibí tu cotización',
    description: 'Múltiples opciones en segundos.',
  },
]
</script>

<template>
  <section 
    class="w-full py-16 sm:py-20 relative"
    style="
      background-image: url('/BgHowItWorks01.jpg');
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
    "
  >
    <!-- Top fade from black -->
    <div class="absolute top-0 left-0 right-0 h-32 bg-gradient-to-b from-black to-transparent pointer-events-none z-10"></div>

    <!-- Bottom fade to black -->
    <div class="absolute bottom-0 left-0 right-0" style="height: 120vh; background: linear-gradient(to top, black, transparent); pointer-events: none; z-index: 10;"></div>

    <div class="w-full px-6 sm:px-12 lg:px-16 relative z-20">
      <!-- Header Section -->
      <div class="text-center">
        <p class="text-sm font-medium text-[#f7f7ad] uppercase tracking-widest mb-4">
          Cómo funciona
        </p>
        <h2 class="text-4xl sm:text-5xl font-black text-white leading-tight mb-4">
          Cotizá tu seguro<br><span style="color: #8fcf9a;">en menos de 1 minuto.</span>
        </h2>
        <p class="text-xl font-medium mb-6 text-white">
          Desde WhatsApp. Sin formularios.
        </p>
        <p class="text-lg text-white/70 max-w-2xl mx-auto">
          Compará coberturas al instante con nuestro asistente inteligente.
        </p>
      </div>

      <!-- Flex Layout: Image + Steps -->
      <div class="flex flex-col lg:flex-row items-center gap-12 lg:gap-16">
        
        <!-- Left Column: Chat Image -->
        <div class="w-full lg:w-1/2 flex justify-center items-center" style="min-height: 800px;">
          <img src="/celular-nuevo.png" alt="Chat WhatsApp" style="max-width: 500px; width: 100%; height: auto;">
        </div>

        <!-- Right Column: Steps Cards -->
        <div class="w-full lg:w-1/2 space-y-6">
          <div v-for="step in steps" :key="step.number" class="group relative rounded-2xl p-6 transition-all duration-300 backdrop-blur-xl overflow-visible" style="background: rgba(255, 255, 255, 0.05); border: 1px solid rgba(255, 255, 255, 0.1);">
            
            <!-- Step Number (Sobresale arriba) -->
            <div class="absolute -top-6 left-6 flex items-center justify-center w-12 h-12 rounded-full text-lg font-black text-white z-20" style="background: linear-gradient(135deg, #8fcf9a 0%, #195d4c 100%);">
              {{ step.number }}
            </div>

            <!-- Content -->
            <div class="pt-4">
              <h3 class="text-lg font-bold text-white mb-2">
                {{ step.title }}
              </h3>
              <p class="text-white/60 text-sm leading-relaxed">
                {{ step.description }}
              </p>
            </div>
          </div>

          <!-- CTA Button -->
          <div class="flex justify-start mt-8">
            <button class="button-glow">
              <div class="button-inner">
                Comenzar ahora
              </div>
            </button>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>

<style scoped>
@keyframes slideBorder {
  0% {
    transform: translateX(-100%);
  }
  100% {
    transform: translateX(100%);
  }
}

.button-glow {
  padding: 0.75rem 1.5rem;
  border-radius: 9999px;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  background-color: #1f1f1f;
  border: none;
  color: white;
  font-weight: bold;
  font-size: 0.875rem;
  cursor: pointer;
}

.button-glow::before {
  content: '';
  position: absolute;
  inset: -10%;
  background-image: linear-gradient(90deg, transparent, rgba(143, 207, 154, 0.8), transparent);
  animation: slideBorder 2s ease-in-out infinite;
  z-index: 1;
}

.button-glow::after {
  content: '';
  position: absolute;
  inset: 1px;
  background-color: #1f1f1f;
  border-radius: 9999px;
  z-index: 2;
}

.button-inner {
  position: relative;
  z-index: 3;
}
</style>
