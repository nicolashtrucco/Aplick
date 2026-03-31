<script setup lang="ts">
import { ref } from 'vue'
import gsap from 'gsap'
import { onMounted } from 'vue'
import Marquee from './ui/marquee/Marquee.vue'
import SeguroCard from './SeguroCard.vue'
import { segurosIndividuales, segurosCorporativos } from '@/data/seguros'

const activeTab = ref<'individuales' | 'corporativos'>('individuales')

const segurosActuales = () => {
  return activeTab.value === 'individuales' ? segurosIndividuales : segurosCorporativos
}

onMounted(() => {
  // Usar Intersection Observer para animar cuando la sección es visible
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting && !entry.target.classList.contains('animated')) {
        entry.target.classList.add('animated')
        animateCoberturas()
      }
    })
  }, { threshold: 0.2 })

  const section = document.querySelector('[data-coberturas-section]')
  if (section) {
    observer.observe(section)
  }
})

const animateCoberturas = () => {
  const tl = gsap.timeline()

  // Animar el título
  tl.from('.coberturas-title', {
    duration: 0.8,
    opacity: 0,
    y: 30,
    ease: 'power3.out'
  }, 0)

  // Animar la descripción
  tl.from('.coberturas-description', {
    duration: 0.8,
    opacity: 0,
    y: 20,
    ease: 'power3.out'
  }, 0.2)

  // Animar las tarjetas con efecto de entrada escalonado
  tl.from('.cobertura-card', {
    duration: 0.8,
    opacity: 0,
    y: 40,
    scale: 0.9,
    stagger: 0.2,
    ease: 'back.out(1.5)'
  }, 0.4)

  // Efecto hover interactivo en las tarjetas
  gsap.utils.toArray('.cobertura-card').forEach((card: any) => {
    card.addEventListener('mouseenter', () => {
      gsap.to(card, { y: -10, duration: 0.3, ease: 'power2.out' })
    })
    card.addEventListener('mouseleave', () => {
      gsap.to(card, { y: 0, duration: 0.3, ease: 'power2.out' })
    })
  })
}
</script>

<template>
  <section class="w-full py-4 pb-0" data-coberturas-section>
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
          <h2 class="coberturas-title text-4xl md:text-5xl lg:text-6xl font-black text-white mb-4">
            Nuestras <span style="color: #8fcf9a;">Coberturas</span>
          </h2>
          <p class="coberturas-description text-white/80 text-base md:text-lg">
            Tenemos la cobertura que necesitás para cada momento de tu vida. Desde seguros individuales hasta soluciones corporativas, te ofrecemos opciones adaptadas a tus necesidades.
          </p>
        </div>

        <!-- Tabs -->
        <!-- <div class="flex justify-center gap-2 sm:gap-4 mb-12 flex-wrap sm:flex-nowrap">
          <button
            @click="activeTab = 'individuales'"
            :class="[
              'px-4 sm:px-6 py-2 sm:py-3 rounded-full font-semibold transition-all duration-300 text-xs sm:text-sm',
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
              'px-4 sm:px-6 py-2 sm:py-3 rounded-full font-semibold transition-all duration-300 text-xs sm:text-sm',
              activeTab === 'corporativos'
                ? 'bg-[#8fcf9a] text-[#195d4c]'
                : 'border-2 border-[#8fcf9a]/50 text-white hover:border-[#8fcf9a]'
            ]"
          >
            Seguros Corporativos
          </button>
        </div> -->

        <!-- Carousel (Full width centered) -->
        <!-- <div class="relative w-full flex-1 flex items-center justify-center overflow-visible pb-16"> -->
            <!-- <Marquee
              pause-on-hover
              :repeat="2"
              class="marquee-coberturas w-full p-0 py-20 [--gap:1rem]"
            >
              <SeguroCard
                v-for="seguro in segurosActuales()"
                :key="seguro.id"
                :title="seguro.title"
                :icon="seguro.icon"
                :iconSize="seguro.iconSize"
              />
            </Marquee> -->

          <!-- Left Gradient (Dark) from page edge -->
          <!-- <div
            class="pointer-events-none fixed inset-y-0 left-0 w-1/6 bg-gradient-to-r from-black to-transparent"
          /> -->

          <!-- Right Gradient (Dark) from page edge -->
          <!-- <div
            class="pointer-events-none fixed inset-y-0 right-0 w-1/6 bg-gradient-to-l from-black to-transparent"
          /> -->
        <!-- </div> -->

        <!-- Featured Cards Section -->
        <div class="relative z-20 px-4 sm:px-6 lg:px-8 md:mt-20 mb-32 md:mb-20">
          <div class="grid grid-cols-1 md:grid-cols-3 gap-8 max-w-6xl mx-auto">
            <!-- Card 1: Seguro Auto -->
            <div class="cobertura-card">
              <SeguroCard
                title="Seguro Automotor"
                icon="/3d-car.png"
                iconSize="h-32 w-32"
              />
            </div>
            <!-- Card 2: Seguro Hogar -->
            <div class="cobertura-card">
              <SeguroCard
                title="Seguro Hogar"
                icon="/documento.webp"
                iconSize="h-24 w-24"
              />
            </div>
            <!-- Card 3: Seguro ART -->
            <div class="cobertura-card">
              <SeguroCard
                title="Seguro Accidente Personal"
                icon="/fabrica.webp"
                iconSize="h-32 w-32"
              />
            </div>
          </div>
        </div>

        <!-- Bottom Black Gradient Overlay -->
        <div class="absolute bottom-0 left-0 right-0 h-32 bg-gradient-to-b from-transparent to-black pointer-events-none z-10"></div>
      </div>
    </div>
  </section>
</template>

<style scoped>
@media (max-width: 1023px) {
  .marquee-coberturas {
    --duration: 40s;
  }
}

@media (min-width: 1024px) {
  .marquee-coberturas {
    --duration: 60s;
  }
}
</style>
