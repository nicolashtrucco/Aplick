<script setup lang="ts">
interface Props {
  icon: string
  title: string
  description: string
}

defineProps<Props>()
</script>

<template>
  <div
    class="group relative min-w-full flex-shrink-0 rounded-2xl p-6 transition-all duration-300 backdrop-blur-xl overflow-visible hover:scale-105"
    style="background: linear-gradient(135deg, rgba(143, 207, 154, 0.1) 0%, rgba(25, 93, 76, 0.1) 100%); border: 2px solid rgba(143, 207, 154, 0.3);"
  >
    <!-- Animated border glow effect -->
    <div 
      class="absolute inset-0 rounded-2xl opacity-0 group-hover:opacity-100 transition-opacity duration-300 pointer-events-none"
      style="
        background: linear-gradient(90deg, transparent, rgba(143, 207, 154, 0.5), transparent);
        animation: slideGlow 2.5s ease-in-out infinite;
      "
    ></div>

    <!-- Icon -->
    <div class="relative z-10 w-12 h-12 rounded-full flex items-center justify-center mb-4 group-hover:scale-110 transition-transform duration-300" style="background: linear-gradient(135deg, #8fcf9a 0%, #195d4c 100%); box-shadow: 0 0 20px rgba(143, 207, 154, 0.3);">
      <i :class="['bi', icon, 'text-white text-base']"></i>
    </div>

    <!-- Content -->
    <h3 class="relative z-10 text-sm font-bold text-white mb-2">
      {{ title }}
    </h3>
    <p class="relative z-10 text-white/60 text-xs leading-relaxed">
      {{ description }}
    </p>
  </div>
</template>

<style scoped>
@keyframes slideGlow {
  0% {
    transform: translateX(-100%);
  }
  100% {
    transform: translateX(100%);
  }
}
</style>
