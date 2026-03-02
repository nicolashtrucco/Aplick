<script setup>
import { ref } from 'vue'

const isOpen = ref(false)

const toggleMenu = () => {
  isOpen.value = !isOpen.value
}
</script>

<template>
  <nav class="fixed top-0 left-0 right-0 z-50 flex justify-center pt-4 px-4">
    <!-- Navbar Container con glassmorphism -->
    <div class="flex items-center justify-between w-full max-w-2xl rounded-full px-6 py-3 transition-all duration-300" style="background: linear-gradient(135deg, rgba(25, 93, 76, 0.15) 0%, rgba(143, 207, 154, 0.08) 100%); border: 1px solid rgba(143, 207, 154, 0.25); backdrop-filter: blur(10px);">
      <!-- Logo -->
      <div class="flex-shrink-0">
        <img src="/public/Logo-Aplick.png" alt="Logo-aplick" class="h-6 w-auto">
      </div>

      <!-- Desktop Navigation -->
      <div class="hidden md:flex space-x-6">
        <a
          href="#"
          class="text-white/80 hover:text-white text-xs font-medium transition-colors"
        >
          Billetera
        </a>
        <a
          href="#"
          class="text-white/80 hover:text-white text-xs font-medium transition-colors"
        >
          Vivi en crypto
        </a>
        <a
          href="#"
          class="text-white/80 hover:text-white text-xs font-medium transition-colors"
        >
          Comunidad
        </a>
        <a
          href="#"
          class="text-white/80 hover:text-white text-xs font-medium transition-colors"
        >
          Aprendé
        </a>
        <a
          href="#"
          class="text-white/80 hover:text-white text-xs font-medium transition-colors"
        >
          Transparencia
        </a>
        <a
          href="#"
          class="text-white/80 hover:text-white text-xs font-medium transition-colors"
        >
          Ayuda
        </a>
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

    <!-- Mobile Navigation -->
    <div v-if="isOpen" class="absolute top-20 left-4 right-4 md:hidden rounded-2xl px-4 py-4 transition-all duration-300" style="background: linear-gradient(135deg, rgba(25, 93, 76, 0.15) 0%, rgba(143, 207, 154, 0.08) 100%); border: 1px solid rgba(143, 207, 154, 0.25); backdrop-filter: blur(10px);">
      <a
        href="#"
        class="text-white/80 hover:text-white block px-3 py-2 rounded-md text-sm font-medium transition-colors"
      >
        Billetera
      </a>
      <a
        href="#"
        class="text-white/80 hover:text-white block px-3 py-2 rounded-md text-sm font-medium transition-colors"
      >
        Vivi en crypto
      </a>
      <a
        href="#"
        class="text-white/80 hover:text-white block px-3 py-2 rounded-md text-sm font-medium transition-colors"
      >
        Comunidad
      </a>
      <a
        href="#"
        class="text-white/80 hover:text-white block px-3 py-2 rounded-md text-sm font-medium transition-colors"
      >
        Aprendé
      </a>
      <a
        href="#"
        class="text-white/80 hover:text-white block px-3 py-2 rounded-md text-sm font-medium transition-colors"
      >
        Transparencia
      </a>
      <a
        href="#"
        class="text-white/80 hover:text-white block px-3 py-2 rounded-md text-sm font-medium transition-colors"
      >
        Ayuda
      </a>
    </div>
  </nav>
</template>

<style scoped>
</style>
