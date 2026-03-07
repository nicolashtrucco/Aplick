<script setup>
import { ref, watch } from 'vue'

const isOpen = ref(false)

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
      height: '96vh'
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
          class="text-white/80 hover:text-white text-sm font-medium transition-colors"
        >
          Inicio
        </a>
        <a
          href="#coberturas"
          class="text-white/80 hover:text-white text-sm font-medium transition-colors"
        >
          Coberturas
        </a>
        <a
          href="#nosotros"
          class="text-white/80 hover:text-white text-sm font-medium transition-colors"
        >
          Nosotros
        </a>
        <a
          href="#como-funciona"
          class="text-white/80 hover:text-white text-sm font-medium transition-colors"
        >
          Cómo Funciona
        </a>
        <a
          href="#ventajas"
          class="text-white/80 hover:text-white text-sm font-medium transition-colors"
        >
          Ventajas
        </a>
      </div>

      <!-- Mobile Navigation -->
      <div v-if="isOpen" class="md:hidden flex flex-col w-full mt-8 pt-3 space-y-1 border-t border-white/10">
        <a
          href="#inicio"
          @click="closeMenu"
          class="text-white/80 hover:text-white block px-3 py-4 rounded-md text-base font-medium transition-colors"
        >
          Inicio
        </a>
        <a
          href="#coberturas"
          @click="closeMenu"
          class="text-white/80 hover:text-white block px-3 py-4 rounded-md text-base font-medium transition-colors"
        >
          Coberturas
        </a>
        <a
          href="#nosotros"
          @click="closeMenu"
          class="text-white/80 hover:text-white block px-3 py-4 rounded-md text-base font-medium transition-colors"
        >
          Nosotros
        </a>
        <a
          href="#como-funciona"
          @click="closeMenu"
          class="text-white/80 hover:text-white block px-3 py-4 rounded-md text-base font-medium transition-colors"
        >
          Cómo Funciona
        </a>
        <a
          href="#ventajas"
          @click="closeMenu"
          class="text-white/80 hover:text-white block px-3 py-4 rounded-md text-base font-medium transition-colors"
        >
          Ventajas
        </a>
      </div>
    </div>
  </nav>
</template>

<style scoped>
</style>
