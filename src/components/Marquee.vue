<script setup lang="ts">
interface Props {
  reverse?: boolean
  pauseOnHover?: boolean
  repeat?: number
}

withDefaults(defineProps<Props>(), {
  reverse: false,
  pauseOnHover: true,
  repeat: 6,
})

const getRepeatedSlots = (count: number) => {
  return Array.from({ length: count }, (_, i) => i)
}
</script>

<template>
  <div
    class="group relative w-full py-20 overflow-hidden"
  >
    <div
      class="flex gap-4 animate-marquee whitespace-nowrap"
      :class="{
        'animate-marquee-reverse': reverse,
        'group-hover:[animation-play-state:paused]': pauseOnHover,
      }"
    >
      <template v-for="i in getRepeatedSlots(repeat)" :key="i">
        <slot />
      </template>
    </div>
  </div>
</template>

<style scoped>
@keyframes marquee {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(calc(-100% - 1rem));
  }
}

@keyframes marquee-reverse {
  from {
    transform: translateX(calc(-100% - 1rem));
  }
  to {
    transform: translateX(0);
  }
}

.animate-marquee {
  animation: marquee linear infinite;
  animation-duration: var(--duration, 20s);
}

.animate-marquee-reverse {
  animation: marquee-reverse linear infinite;
  animation-duration: var(--duration, 20s);
}
</style>
