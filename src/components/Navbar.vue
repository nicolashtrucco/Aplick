<script setup>
import { ref, watch, onMounted, onUnmounted } from 'vue'

const isOpen = ref(false)
const activeSection = ref('inicio')
let observer = null

const toggleMenu = () => {
  isOpen.value = !isOpen.value
}

const closeMenu = () => {
  isOpen.value = false
}

watch(isOpen, (newVal) => {
  if (newVal) {
    document.body.style.overflow = 'hidden'
  } else {
    document.body.style.overflow = 'auto'
  }
})

const isLinkActive = (sectionId) => {
  return activeSection.value === sectionId
}

const handleLinkClick = (sectionId) => {
  activeSection.value = sectionId
}

onMounted(() => {
  // Escuchar eventos de scroll para detectar la sección activa
  const handleScroll = () => {
    const sections = document.querySelectorAll('section[id]')
    let currentSection = 'inicio'
    
    sections.forEach((section) => {
      const rect = section.getBoundingClientRect()
      // Si la sección está en la parte superior de la pantalla
      if (rect.top <= 150) {
        currentSection = section.id
      }
    })
    
    activeSection.value = currentSection
  }

  window.addEventListener('scroll', handleScroll)
  
  onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll)
  })
})

</script>

<template>
  <nav class="fixed top-0 left-0 right-0 z-50 flex justify-center pt-4 pb-4 px-4 md:pt-4 md:pb-0 md:px-4" :class="isOpen ? 'md:h-auto h-screen' : 'h-auto'">
    <!-- Navbar Container con glassmorphism -->
    <div :class="[
      'flex w-full transition-all duration-300 rounded-2xl md:rounded-full',
      isOpen ? 'md:max-w-2xl md:flex-row flex-col md:items-center md:justify-between md:py-3 py-3 md:px-6 px-6 items-start' : 'max-w-2xl flex-row items-center justify-between py-3 px-6'
    ]" :style="isOpen ? {
      background: 'linear-gradient(135deg, rgba(0, 0, 0, 0.15) 0%, rgba(128, 128, 128, 0.08) 100%)',
      border: '1px solid rgba(255, 255, 255, 0.15)',
      backdropFilter: 'blur(10px)',
      width: '100%',
      height: '96dvh',
      display: 'flex',
      flexDirection: 'column'
    } : {
      background: 'linear-gradient(135deg, rgba(0, 0, 0, 0.15) 0%, rgba(128, 128, 128, 0.08) 100%)',
      border: '1px solid rgba(255, 255, 255, 0.15)',
      backdropFilter: 'blur(10px)'
    }">
      <!-- Header row: Logo and menu button -->
      <div class="flex items-center justify-between w-full md:w-auto">
        <!-- Logo -->
        <div class="shrink-0">
          <img src="/Logo-Aplick.png" alt="Logo-aplick" class="h-6 w-auto">
        </div>

        <!-- Mobile menu button -->
        <div class="md:hidden">
          <button
            @click="toggleMenu"
            class="inline-flex items-center justify-center p-2 rounded-full text-white transition-colors"
            style="background: rgba(143, 207, 154, 0.1);"
          >
            <svg
              class="h-5 w-5"
              stroke="currentColor"
              fill="none"
              viewBox="0 0 24 24"
            >
              <path
                v-if="!isOpen"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M4 6h16M4 12h16M4 18h16"
              />
              <path
                v-else
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M6 18L18 6M6 6l12 12"
              />
            </svg>
          </button>
        </div>
      </div>

      <!-- Desktop Navigation -->
      <div class="hidden md:flex space-x-8">
        <a
          href="#inicio"
          @click="handleLinkClick('inicio')"
          :class="isLinkActive('inicio') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="text-sm font-medium transition-colors"
        >
          Inicio
        </a>
        <a
          href="#coberturas"
          @click="handleLinkClick('coberturas')"
          :class="isLinkActive('coberturas') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="text-sm font-medium transition-colors"
        >
          Coberturas
        </a>
        <a
          href="#nosotros"
          @click="handleLinkClick('nosotros')"
          :class="isLinkActive('nosotros') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="text-sm font-medium transition-colors"
        >
          Nosotros
        </a>
        <a
          href="#como-funciona"
          @click="handleLinkClick('como-funciona')"
          :class="isLinkActive('como-funciona') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="text-sm font-medium transition-colors"
        >
          Cómo Funciona
        </a>
        <a
          href="#ventajas"
          @click="handleLinkClick('ventajas')"
          :class="isLinkActive('ventajas') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="text-sm font-medium transition-colors"
        >
          Ventajas
        </a>
      </div>

      <!-- Mobile Navigation -->
      <div v-if="isOpen" class="md:hidden flex flex-col w-full mt-8 pt-3 space-y-1 border-t border-white/10 flex-1">
        <a
          href="#inicio"
          @click="closeMenu(); handleLinkClick('inicio')"
          :class="isLinkActive('inicio') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="block px-3 py-4 rounded-md text-lg font-medium transition-colors"
        >
          Inicio
        </a>
        <a
          href="#coberturas"
          @click="closeMenu(); handleLinkClick('coberturas')"
          :class="isLinkActive('coberturas') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="block px-3 py-4 rounded-md text-lg font-medium transition-colors"
        >
          Coberturas
        </a>
        <a
          href="#nosotros"
          @click="closeMenu(); handleLinkClick('nosotros')"
          :class="isLinkActive('nosotros') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="block px-3 py-4 rounded-md text-lg font-medium transition-colors"
        >
          Nosotros
        </a>
        <a
          href="#como-funciona"
          @click="closeMenu(); handleLinkClick('como-funciona')"
          :class="isLinkActive('como-funciona') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="block px-3 py-4 rounded-md text-lg font-medium transition-colors"
        >
          Cómo Funciona
        </a>
        <a
          href="#ventajas"
          @click="closeMenu(); handleLinkClick('ventajas')"
          :class="isLinkActive('ventajas') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="block px-3 py-4 rounded-md text-lg font-medium transition-colors"
        >
          Ventajas
        </a>

        <!-- CTA Button -->
        <div class="flex justify-start mt-auto pt-6 pb-3 w-full">
          <button class="button-glow w-full">
            <div class="button-inner">
              Comenzar ahora
            </div>
          </button>
        </div>
      </div>
    </div>
  </nav>
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
