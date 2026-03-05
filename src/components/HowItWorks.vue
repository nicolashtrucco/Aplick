<script setup>
const steps = [
  {
    number: 1,
    title: 'Escribinos',
    description: 'Iniciá una conversación con nuestro asistente IA.',
  },
  {
    number: 2,
    title: 'Respondé 3 preguntas',
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
  <section class="w-full py-4">
    <div class="w-full">
      <!-- Main Container with Radial Gradient -->
      <div 
        class="rounded-3xl overflow-hidden"
        style="
          background-image: url('/BgHowItWorks01.jpg');
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
            <h2 class="text-4xl sm:text-5xl font-black text-white leading-tight mb-4">
              Cotizá tu seguro<br><span style="color: #8fcf9a;">en menos de 1 minuto.</span>
            </h2>
            <p class="text-xl font-semibold mb-6" style="color: #8fcf9a;">
              Desde WhatsApp. Sin formularios.
            </p>
            <p class="text-lg text-white/70 max-w-2xl mx-auto">
              Compará coberturas al instante con nuestro asistente inteligente.
            </p>
          </div>

          <!-- Flex Layout: Image + Steps -->
          <div class="flex flex-col lg:flex-row items-center gap-12 lg:gap-16">
            
            <!-- Left Column: Chat Image -->
            <div class="w-full lg:w-1/2 flex justify-center">
              <img src="/ChatWsp.png" alt="Chat WhatsApp" class="max-w-sm w-full h-auto rounded-3xl shadow-2xl">
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
                <button class="px-8 py-4 bg-[#8fcf9a] text-[#195d4c] font-bold text-lg rounded-full hover:bg-[#f7f7ad] transition-all duration-300 shadow-lg hover:shadow-xl">
                  Comenzar ahora
                </button>
              </div>
            </div>

          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
</style>
