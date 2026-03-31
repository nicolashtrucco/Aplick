<script setup lang="ts">
import gsap from 'gsap'
import { onMounted } from 'vue'

const features = [
  {
    icon: '/Rayo.png',
    title: 'Simple y Rápido',
    description: 'Cotiza tu seguro en segundos sin formularios complejos. Tecnología IA que entiende tus necesidades.',
  },
  {
    icon: '/Money.webp',
    title: 'Accesible y Confiable',
    description: 'Seguros verificados y regulados. Protección real con transparencia total en cada paso.',
  },
  {
    icon: '/Chat.png',
    title: 'Asistente IA 24/7',
    description: 'Nuestro chatbot inteligente en WhatsApp responde tus preguntas cuando las necesitas.',
  },
  {
    icon: '/Check.png',
    title: 'Mejores Precios',
    description: 'Comparamos opciones para traerte las mejores coberturas al mejor precio del mercado.',
  },
]

onMounted(() => {
  // Usar Intersection Observer para animar cuando la sección es visible
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting && !entry.target.classList.contains('animated')) {
        entry.target.classList.add('animated')
        animateAboutAplick()
      }
    })
  }, { threshold: 0.2 })

  const section = document.querySelector('[data-about-section]')
  if (section) {
    observer.observe(section)
  }
})

const animateAboutAplick = () => {
  const tl = gsap.timeline()

  // Animar etiqueta "Sobre Aplick"
  tl.from('.about-label', {
    duration: 0.6,
    opacity: 0,
    y: 20,
    ease: 'power3.out'
  }, 0)

  // Animar el título
  tl.from('.about-title', {
    duration: 0.8,
    opacity: 0,
    y: 30,
    ease: 'power3.out'
  }, 0.2)

  // Animar el párrafo de descripción
  tl.from('.about-description', {
    duration: 0.8,
    opacity: 0,
    y: 25,
    ease: 'power3.out'
  }, 0.4)

  // Animar las tarjetas de features con efecto de entrada
  gsap.set('.feature-card', { opacity: 0, y: 50, scale: 0.9 })
  tl.to('.feature-card', {
    duration: 0.8,
    opacity: 1,
    y: 0,
    scale: 1,
    stagger: 0.15,
    ease: 'back.out(1.5)'
  }, 0.6)

  // Animar iconos con rotación
  tl.from('.feature-icon', {
    duration: 0.8,
    opacity: 0,
    rotation: -180,
    scale: 0,
    stagger: 0.15,
    ease: 'back.out(1.7)'
  }, 0.7)

  // Efecto hover interactivo en las tarjetas
  const cards = gsap.utils.toArray('.feature-card') as HTMLElement[]
  cards.forEach((card) => {
    const icon = card.querySelector('.feature-icon') as HTMLElement
    
    card.addEventListener('mouseenter', () => {
      gsap.to(card, { y: -15, duration: 0.3, ease: 'power2.out' })
      if (icon) gsap.to(icon, { rotation: 360, duration: 0.6, ease: 'back.out(1.7)' })
    })
    
    card.addEventListener('mouseleave', () => {
      gsap.to(card, { y: 0, duration: 0.3, ease: 'power2.out' })
      if (icon) gsap.to(icon, { rotation: 0, duration: 0.6, ease: 'back.out(1.7)' })
    })
  })
}
</script>

<template>
  <section 
    class="w-full py-16 sm:py-20 relative"
    data-about-section
    style="
      background-image: url('/BgAboutAplick01.jpg');
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
    "
  >
    <!-- Top fade from black -->
    <div class="absolute top-0 left-0 right-0 h-32 bg-gradient-to-b from-black to-transparent pointer-events-none z-10"></div>

    <!-- Bottom fade to black -->
    <div class="absolute bottom-0 left-0 right-0 h-32 bg-gradient-to-t from-black to-transparent pointer-events-none z-10"></div>
    <div class="w-full px-6 sm:px-12 lg:px-16 relative z-20">
      <!-- Two Column Layout -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-start mb-12">
        
        <!-- Left Column: Content -->
        <div class="max-w-3xl">
          <p class="about-label text-sm font-medium text-[#f7f7ad] uppercase tracking-widest mb-4">
            Sobre Aplick
          </p>
          <h2 class="about-title text-4xl sm:text-5xl font-black text-white leading-tight mb-6">
            La tecnología que <span style="color: #8fcf9a;">simplifica los seguros</span>
          </h2>
          <p class="about-description text-lg text-white/70 leading-relaxed">
            APLICK es una plataforma digital que transforma la experiencia de cotizar seguros. Utilizamos inteligencia artificial integrada en WhatsApp para eliminar la complejidad tradicional del mundo de los seguros. Nuestro objetivo es convertir una tarea tediosa en algo simple, rápido y accesible para todos.
          </p>
        </div>

        <!-- Right Column: Empty (para mantener layout) -->
        <div></div>
      </div>

      <!-- Features Grid (debajo del texto, full width) -->
            <div class="grid grid-cols-1 md:grid-cols-4 gap-6">
              <div v-for="(feature, index) in features" :key="index" class="feature-card group relative rounded-2xl p-6 transition-all duration-300 backdrop-blur-xl hover:scale-105 overflow-visible" style="background: rgba(255, 255, 255, 0.05); border: 1px solid rgba(255, 255, 255, 0.1);">
                <!-- Icon Image (Sobresale arriba) -->
                <div class="feature-icon absolute -top-8 left-1/2 -translate-x-1/2 w-16 h-16 flex items-center justify-center z-20 pointer-events-none">
                  <img 
                    :src="feature.icon" 
                    :alt="feature.title" 
                    class="h-full w-full object-contain drop-shadow-lg"
                  />
                </div>

                <!-- Content (con espacio arriba para la imagen) -->
                <div class="flex flex-col items-center text-center pt-6">
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
  </section>
</template>

<style scoped>
@import url('https://cdn.jsdelivr.net/npm/bootstrap-icons@1.13.1/font/bootstrap-icons.css');
</style>
