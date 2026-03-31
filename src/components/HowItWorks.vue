<script setup lang="ts">
import gsap from 'gsap'
import { onMounted } from 'vue'

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

onMounted(() => {
  // Usar Intersection Observer para animar cuando la sección es visible
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting && !entry.target.classList.contains('animated')) {
        entry.target.classList.add('animated')
        animateHowItWorks()
      }
    })
  }, { threshold: 0.2 })

  const section = document.querySelector('[data-howitworks-section]')
  if (section) {
    observer.observe(section)
  }
})

const animateHowItWorks = () => {
  const tl = gsap.timeline()

  // Animar etiqueta
  tl.from('.howitworks-label', {
    duration: 0.6,
    opacity: 0,
    y: 20,
    ease: 'power3.out'
  }, 0)

  // Animar título
  tl.from('.howitworks-title', {
    duration: 0.8,
    opacity: 0,
    y: 30,
    ease: 'power3.out'
  }, 0.2)

  // Animar subtítulo
  tl.from('.howitworks-subtitle', {
    duration: 0.8,
    opacity: 0,
    y: 20,
    ease: 'power3.out'
  }, 0.4)

  // Animar descripción
  tl.from('.howitworks-description', {
    duration: 0.8,
    opacity: 0,
    y: 15,
    ease: 'power3.out'
  }, 0.6)

  // Animar tarjetas de pasos
  gsap.set('.step-card', { opacity: 0, y: 50, scale: 0.9 })
  tl.to('.step-card', {
    duration: 0.8,
    opacity: 1,
    y: 0,
    scale: 1,
    stagger: 0.2,
    ease: 'back.out(1.5)'
  }, 0.8)

  // Animar números de pasos con efecto de conteo
  tl.from('.step-number', {
    duration: 0.8,
    opacity: 0,
    scale: 0,
    rotation: -180,
    stagger: 0.2,
    ease: 'back.out(1.7)'
  }, 0.9)

  // Animar botón CTA
  gsap.set('.howitworks-button', { opacity: 0, y: 30, scale: 0.8 })
  tl.to('.howitworks-button', {
    duration: 0.6,
    opacity: 1,
    y: 0,
    scale: 1,
    ease: 'back.out(1.5)'
  }, 1.3)

  // Efecto hover en las tarjetas
  const cards = gsap.utils.toArray('.step-card') as HTMLElement[]
  cards.forEach((card) => {
    card.addEventListener('mouseenter', () => {
      gsap.to(card, { y: -15, duration: 0.3, ease: 'power2.out' })
      gsap.to(card.querySelector('.step-number'), { scale: 1.15, duration: 0.3, ease: 'back.out(1.7)' })
    })
    card.addEventListener('mouseleave', () => {
      gsap.to(card, { y: 0, duration: 0.3, ease: 'power2.out' })
      gsap.to(card.querySelector('.step-number'), { scale: 1, duration: 0.3, ease: 'back.out(1.7)' })
    })
  })

  // Efecto pulsante en el botón
  gsap.to('.howitworks-button', {
    duration: 2,
    boxShadow: '0 0 30px rgba(143, 207, 154, 0.8)',
    repeat: -1,
    yoyo: true,
    ease: 'sine.inOut'
  })
}
</script>

<template>
  <section 
    class="w-full py-16 sm:py-20 relative"
    data-howitworks-section
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
        <p class="howitworks-label text-sm font-medium text-[#f7f7ad] uppercase tracking-widest mb-4">
          Cómo funciona
        </p>
        <h2 class="howitworks-title text-4xl sm:text-5xl font-black text-white leading-tight mb-4">
          Cotizá tu seguro<br><span style="color: #8fcf9a;">en menos de 1 minuto.</span>
        </h2>
        <p class="howitworks-subtitle text-xl font-medium mb-6 text-white">
          Desde WhatsApp. Sin formularios.
        </p>
        <p class="howitworks-description text-lg text-white/70 max-w-2xl mx-auto">
          Compará coberturas al instante con nuestro asistente inteligente.
        </p>
      </div>

      <!-- Flex Layout: Image + Steps -->
      <div class="flex flex-col lg:flex-row items-center justify-center gap-12 lg:gap-16">
        
        <!-- Left Column: Chat Image -->
        <!-- <div class="w-full lg:w-1/2 flex justify-center items-center" style="min-height: 800px;">
          <img src="/celular-nuevo01.png" alt="Chat WhatsApp" style="max-width: 350px; width: 100%; height: auto;">
        </div> -->

        <!-- Right Column: Steps Cards -->
        <div class="w-full lg:w-1/2 space-y-6 flex flex-col mt-10">
          <div v-for="step in steps" :key="step.number" class="step-card group relative rounded-2xl p-6 transition-all duration-300 backdrop-blur-xl overflow-hidden">
            
            <!-- Content with Step Number -->
            <div class="relative z-10">
              <!-- Step Number and Title -->
              <div class="flex items-start gap-3">
                <div class="flex items-center justify-center w-10 h-10 rounded-full text-sm font-black text-white shrink-0 mt-0.5" style="background: linear-gradient(135deg, #8fcf9a 0%, #195d4c 100%);">
                  {{ step.number }}
                </div>
                <div>
                  <h3 class="text-lg font-bold text-white mb-0">
                    {{ step.title }}
                  </h3>
                  <!-- Description -->
                  <p class="text-white/60 text-sm leading-relaxed mt-1">
                    {{ step.description }}
                  </p>
                </div>
              </div>

            </div>
          </div>

          <!-- CTA Button -->
          <div class="flex justify-center mt-8">
            <button class="howitworks-button button-glow">
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

/* .button-glow::before {
  content: '';
  position: absolute;
  inset: -10%;
  background-image: linear-gradient(90deg, transparent, rgba(143, 207, 154, 0.8), transparent);
  animation: slideBorder 2s ease-in-out infinite;
  z-index: 1;
} */

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

.step-card {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  position: relative;
}

.step-card::before {
  content: '';
  position: absolute;
  inset: 0;
  padding: 1px;
  background: linear-gradient(90deg, transparent, rgba(143, 207, 154, 0.8), transparent);
  border-radius: 1rem;
  animation: slideBorder 2s ease-in-out infinite;
  z-index: -1;
  -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
}
</style>
