<script setup lang="ts">
import { ref } from 'vue'
import Marquee from './Marquee.vue'
import SeguroCard from './SeguroCard.vue'
import { segurosIndividuales, segurosCorporativos } from '@/data/seguros'

const activeTab = ref<'individuales' | 'corporativos'>('individuales')

const segurosActuales = () => {
  return activeTab.value === 'individuales' ? segurosIndividuales : segurosCorporativos
}
</script>

<template>
  <section 
    class="relative w-full h-screen flex flex-col items-center justify-center overflow-hidden"
    style="background: linear-gradient(180deg, rgba(0, 0, 0, 0.3) 0%, rgba(25, 93, 76, 0.15) 10%, rgba(143, 207, 154, 0.08) 50%, rgba(25, 93, 76, 0.15) 90%, rgba(0, 0, 0, 0.3) 100%);"
  >
    <!-- Background gradient overlay -->
    <div class="absolute inset-0 opacity-20" style="background: linear-gradient(135deg, rgba(25, 93, 76, 0.2) 0%, rgba(143, 207, 154, 0.1) 100%);"></div>
    <!-- Header & Tabs (Centered content) -->
    <div class="w-full flex flex-col items-center justify-start pt-16 px-4 sm:px-6 lg:px-8">
      <!-- Header -->
      <div class="text-center mb-8 max-w-2xl">
        <h2 class="text-4xl md:text-5xl lg:text-6xl font-black text-white mb-4">
          Nuestras <span style="color: #8fcf9a;">Coberturas</span>
        </h2>
        <p class="text-white/80 text-base md:text-lg">
          Tenemos la cobertura que necesitás para cada momento de tu vida. Desde seguros individuales hasta soluciones corporativas, te ofrecemos opciones adaptadas a tus necesidades.
        </p>
      </div>

      <!-- Tabs -->
      <div class="flex justify-center gap-4 mb-12">
        <button
          @click="activeTab = 'individuales'"
          :class="[
            'px-6 py-3 rounded-full font-semibold transition-all duration-300',
            activeTab === 'individuales'
              ? 'bg-[#8fcf9a] text-[#195d4c]'
              : 'border-2 border-[#8fcf9a]/50 text-white hover:border-[#8fcf9a]'
          ]"
        >
          Seguros Individuales
        </button>
        <button
          @click="activeTab = 'corporativos'"
          :class="[
            'px-6 py-3 rounded-full font-semibold transition-all duration-300',
            activeTab === 'corporativos'
              ? 'bg-[#8fcf9a] text-[#195d4c]'
              : 'border-2 border-[#8fcf9a]/50 text-white hover:border-[#8fcf9a]'
          ]"
        >
          Seguros Corporativos
        </button>
      </div>
    </div>

    <!-- Carousel (Full width centered) -->
    <div class="relative w-full flex-1 flex items-center justify-center overflow-visible">
      <Marquee
        pause-on-hover
        class="[--duration:30s] w-full"
      >
        <SeguroCard
          v-for="seguro in segurosActuales()"
          :key="seguro.id"
          :title="seguro.title.replace('Cotizar Seguro ', '')"
          :icon="seguro.icon"
          :iconSize="seguro.iconSize"
        />
      </Marquee>

      <!-- Left Gradient (Dark) from page edge -->
      <div
        class="pointer-events-none fixed inset-y-0 left-0 w-1/6 bg-gradient-to-r from-black to-transparent"
      />

      <!-- Right Gradient (Dark) from page edge -->
      <div
        class="pointer-events-none fixed inset-y-0 right-0 w-1/6 bg-gradient-to-l from-black to-transparent"
      />
    </div>
  </section>
</template>
