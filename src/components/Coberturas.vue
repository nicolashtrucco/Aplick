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
  <section class="w-full py-4 pb-0">
    <div class="w-full">
      <!-- Main Container with Background Image -->
      <div 
        class="rounded-3xl overflow-hidden relative"
        style="
          background-image: url('/BgCoberturas.jpg');
          background-size: cover;
          background-position: center;
          background-repeat: no-repeat;
        "
      >
        <!-- Top Black Gradient Overlay -->
        <div class="absolute top-0 left-0 right-0 h-32 bg-gradient-to-b from-black/80 via-black/40 to-transparent pointer-events-none z-10"></div>
        <!-- Header -->
        <div class="text-center mb-8 max-w-2xl mx-auto px-4 sm:px-6 lg:px-8 pt-16">
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

        <!-- Carousel (Full width centered) -->
        <div class="relative w-full flex-1 flex items-center justify-center overflow-visible pb-16">
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

        <!-- Bottom Black Gradient Overlay -->
        <div class="absolute bottom-0 left-0 right-0 h-32 bg-gradient-to-b from-transparent to-black pointer-events-none z-10"></div>
      </div>
    </div>
  </section>
</template>
