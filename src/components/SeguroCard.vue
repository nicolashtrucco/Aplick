<script setup lang="ts">
interface Props {
  title: string
  icon: string
  iconSize?: string
}

withDefaults(defineProps<Props>(), {
  iconSize: "h-32 w-32"
})
</script>

<template>
  <div
    class="seguro-card relative flex flex-col items-center justify-end px-6 py-4 rounded-2xl border border-[#8fcf9a]/50 transition-all duration-300 hover:border-[#8fcf9a]/70 overflow-visible"
    style="background: radial-gradient(circle at center bottom, rgba(143, 207, 154, 0.25) 0%, rgba(25, 93, 76, 0.15) 35%, rgba(26, 26, 26, 0.9) 100%); backdrop-filter: blur(12px);"
  >
    <!-- Icon (Sobresale arriba) -->
    <div :class="`absolute -top-12 ${iconSize} flex items-center justify-center z-20 pointer-events-none`">
      <img 
        :src="icon" 
        alt="Icono seguro" 
        class="h-full w-full object-contain drop-shadow-lg"
      />
    </div>
    
    <!-- Title -->
    <p class="text-white/90 font-semibold text-base leading-snug text-center max-w-xs relative z-10">{{ title }}</p>
  </div>
</template>

<style scoped>
@media (max-width: 1023px) {
  .seguro-card {
    min-width: 200px !important;
    height: 120px !important;
    padding: 12px 16px !important;
  }

  .seguro-card p {
    font-size: 12px;
  }
}

@media (min-width: 1024px) {
  .seguro-card {
    min-width: 300px;
    height: 160px;
  }

  .seguro-card p {
    font-size: 16px;
  }
}
</style>
