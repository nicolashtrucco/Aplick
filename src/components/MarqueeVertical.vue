<script setup lang="ts">
interface Props {
  reverse?: boolean
  pauseOnHover?: boolean
  repeat?: number
  mobileOptimized?: boolean
}

withDefaults(defineProps<Props>(), {
  reverse: false,
  pauseOnHover: true,
  repeat: 6,
  mobileOptimized: false,
})

const getRepeatedSlots = (count: number) => {
  return Array.from({ length: count }, (_, i) => i)
}
</script>

<template>
  <div
    class="group relative w-full h-full flex flex-col"
  >
    <div class="overflow-hidden w-full h-full">
      <div
        class="flex flex-col gap-4 lg:gap-4 animate-marquee-vertical"
        :class="{
          'animate-marquee-vertical-reverse': reverse,
          'group-hover:[animation-play-state:paused]': pauseOnHover,
          'gap-1': mobileOptimized,
        }"
      >
        <template v-for="i in getRepeatedSlots(repeat)" :key="i">
          <slot />
        </template>
      </div>
    </div>
  </div>
</template>

<style scoped>
@keyframes marquee-vertical {
  from {
    transform: translateY(0);
  }
  to {
    transform: translateY(calc(-100% - 1rem));
  }
}

@keyframes marquee-vertical-reverse {
  from {
    transform: translateY(calc(-100% - 1rem));
  }
  to {
    transform: translateY(0);
  }
}

.animate-marquee-vertical {
  animation: marquee-vertical 45s linear infinite;
  animation-duration: var(--duration, 45s);
}

.animate-marquee-vertical-reverse {
  animation: marquee-vertical-reverse 45s linear infinite;
  animation-duration: var(--duration, 45s);
}
</style>
