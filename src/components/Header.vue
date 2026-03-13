<script setup>
import Aurora from './Aurora/Aurora.vue'
</script>

<template>
  <header class="w-full">

    <!-- Hero Section -->
    <section 
  class="relative w-full h-screen flex flex-col items-center justify-center overflow-hidden rounded-3xl">
        <Aurora
          :color-stops="['#000000', '#3F6F4A', '#000000']"
          :amplitude="1.0"
          :blend="0.5"
          :speed="1.0"
          :intensity="1.0"
          class="absolute inset-0 w-full h-full"
        />


      <!-- Hero Content -->
      <div class="relative z-10 max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center py-16 md:py-24">
        <!-- Main Title -->
        <div class="hero-title">
          <h1 class="text-4xl md:text-5xl lg:text-6xl font-black text-white leading-tight mb-2">
            <span class="text-white">LA </span>
            <span style="color: #8fcf9a;">FORMA</span>
            <br>
            <span style="color: #8fcf9a;">INTELIGENTE</span>
            <span class="text-white"> DE</span>
            <br>
            <span class="text-white">ASEGURAR</span>
          </h1>
        </div>

        <!-- Description -->
        <div class="hero-description mt-6">
          <p class="text-base md:text-lg text-white/80 max-w-2xl mx-auto leading-relaxed">
            <span class="block text-base md:text-lg font-semibold mb-2" style="color: #8fcf9a;">
              Inteligencia en seguros.
            </span>
            Una nueva forma de cotizar, simple, inmediata y 100% digital.
          </p>
        </div>

        <!-- CTA Buttons -->
        <div class="hero-buttons mt-8 flex flex-col sm:flex-row gap-3 justify-center items-center">
          <button class="px-6 py-3 bg-white text-[#195d4c] font-bold text-sm rounded-full hover:bg-[#f7f7ad] transition-all duration-300 shadow-lg hover:shadow-xl">
            Cotizar seguro
          </button>
          <button class="button-glow">
            <div class="button-inner">
              Llegó tu Asistente IA
              <span class="ml-2">→</span>
            </div>
          </button>
        </div>
      </div>
    </section>
  </header>
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
  background-color: black;
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
  background-color: black;
  border-radius: 9999px;
  z-index: 2;
}

.button-inner {
  position: relative;
  z-index: 3;
}

</style>
