<script setup lang="ts">
interface Props {
  reverse?: boolean
  pauseOnHover?: boolean
}

withDefaults(defineProps<Props>(), {
  reverse: false,
  pauseOnHover: true,
})
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
      <slot />
      <slot />
      <slot />
      <slot />
      
    </div>
  </div>
</template>

<style scoped>
@keyframes marquee {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(-100%);
  }
}

@keyframes marquee-reverse {
  from {
    transform: translateX(-100%);
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
