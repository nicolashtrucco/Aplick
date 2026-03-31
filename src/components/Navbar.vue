<script setup lang="ts">
import gsap from 'gsap'
import { ref, watch, onMounted, onUnmounted } from 'vue'

const isOpen = ref(false)
const activeSection = ref('inicio')

const toggleMenu = () => {
  isOpen.value = !isOpen.value
}

const closeMenu = () => {
  isOpen.value = false
}

const isLinkActive = (sectionId: string) => {
  return activeSection.value === sectionId
}

const handleLinkClick = (
  sectionId: string,
  event?: MouseEvent,
  shouldCloseMenu = false,
) => {
  activeSection.value = sectionId

  const clickedLink = event?.currentTarget as HTMLElement | null
  if (clickedLink) {
    gsap.fromTo(
      clickedLink,
      { scale: 1 },
      {
        scale: 0.96,
        duration: 0.12,
        ease: 'power2.out',
        yoyo: true,
        repeat: 1,
      },
    )
  }

  if (shouldCloseMenu) {
    closeMenu()
  }

  const targetSection = document.getElementById(sectionId)
  if (!targetSection) return

  const navbar = document.querySelector('nav')
  const navbarHeight = navbar?.getBoundingClientRect().height ?? 0
  const sectionTop =
    window.scrollY +
    targetSection.getBoundingClientRect().top -
    navbarHeight -
    20

  window.scrollTo({
    top: Math.max(sectionTop, 0),
    behavior: 'smooth',
  })

  window.history.replaceState(null, '', `#${sectionId}`)
}

onMounted(() => {
  animateNavbarOnLoad()

  // Escuchar eventos de scroll para detectar la sección activa
  const handleScroll = () => {
    const sections = document.querySelectorAll('section[id]')
    let currentSection = 'inicio'

    sections.forEach((section) => {
      const rect = section.getBoundingClientRect()
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

const animateNavbarOnLoad = () => {
  const desktopNav = document.querySelector('.hidden.md\\:flex')
  const logo = document.querySelector('nav img')
  const mobileButton = document.querySelector('[data-navbar-toggle]')

  gsap.from([logo, mobileButton].filter(Boolean), {
    opacity: 0,
    y: -12,
    duration: 0.6,
    stagger: 0.08,
    ease: 'power2.out',
  })

  if (desktopNav) {
    const links = desktopNav.querySelectorAll('a')
    gsap.from(links, {
      opacity: 0,
      y: -15,
      duration: 0.5,
      stagger: 0.1,
      delay: 0.3,
      ease: 'power2.out',
    })

    // Add hover effects to desktop links
    links.forEach((link) => {
      link.addEventListener('mouseenter', () => {
        gsap.to(link, {
          y: -3,
          duration: 0.3,
          ease: 'power2.out',
        })
      })
      link.addEventListener('mouseleave', () => {
        gsap.to(link, {
          y: 0,
          duration: 0.3,
          ease: 'power2.out',
        })
      })
    })
  }

  const mobileNavContainer = document.querySelector('[data-mobile-nav]')
  if (mobileNavContainer) {
    const mobileLinks = mobileNavContainer.querySelectorAll('a')
    mobileLinks.forEach((link) => {
      gsap.set(link, { opacity: 0, x: -20 })
    })

    mobileLinks.forEach((link) => {
      link.addEventListener('mouseenter', () => {
        gsap.to(link, {
          x: 5,
          duration: 0.3,
          ease: 'power2.out',
        })
      })
      link.addEventListener('mouseleave', () => {
        gsap.to(link, {
          x: 0,
          duration: 0.3,
          ease: 'power2.out',
        })
      })
    })
  }
}

watch(isOpen, (newVal) => {
  document.body.style.overflow = newVal ? 'hidden' : 'auto'

  if (newVal) {
    setTimeout(() => {
      const mobileNavContainer = document.querySelector('[data-mobile-nav]')
      if (mobileNavContainer) {
        const mobileLinks = mobileNavContainer.querySelectorAll('.navbar-mobile-link')

        mobileLinks.forEach((link, index) => {
          gsap.fromTo(
            link,
            {
              opacity: 0,
              x: -30,
              rotationZ: -5,
            },
            {
              opacity: 1,
              x: 0,
              rotationZ: 0,
              duration: 0.5,
              delay: index * 0.08,
              ease: 'elastic.out(1, 0.5)',
            },
          )
        })

        const ctaButton = mobileNavContainer.querySelector('.navbar-cta-button')
        if (ctaButton) {
          gsap.fromTo(
            ctaButton,
            {
              opacity: 0,
              y: 20,
              scale: 0.9,
            },
            {
              opacity: 1,
              y: 0,
              scale: 1,
              duration: 0.5,
              delay: mobileLinks.length * 0.08 + 0.1,
              ease: 'back.out(1.7)',
            },
          )
        }
      }
    }, 100)
  }
}, { flush: 'post' })
</script>

<template>
  <nav class="fixed top-0 left-0 right-0 z-9999 flex justify-center pt-4 pb-4 px-4 md:pt-4 md:pb-0 md:px-4" :class="isOpen ? 'md:h-auto h-screen' : 'h-auto'">
    <!-- Navbar Container con glassmorphism -->
    <div :class="[
      'flex w-full transition-all duration-300 rounded-2xl md:rounded-full',
      isOpen ? 'md:max-w-2xl md:flex-row flex-col md:items-center md:justify-between md:py-3 py-3 md:px-6 px-6 items-start' : 'max-w-2xl flex-row items-center justify-between py-3 px-6'
    ]" data-navbar-glass :style="isOpen ? {
      background: 'linear-gradient(135deg, rgba(0, 0, 0, 0.25) 0%, rgba(128, 128, 128, 0.12) 100%)',
      border: '1px solid rgba(255, 255, 255, 0.2)',
      backdropFilter: 'blur(10px)',
      WebkitBackdropFilter: 'blur(10px)',
      width: '100%',
      height: '96dvh',
      display: 'flex',
      flexDirection: 'column'
    } : {
      background: 'linear-gradient(135deg, rgba(0, 0, 0, 0.25) 0%, rgba(128, 128, 128, 0.12) 100%)',
      border: '1px solid rgba(255, 255, 255, 0.2)',
      backdropFilter: 'blur(10px)',
      WebkitBackdropFilter: 'blur(10px)'
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
            data-navbar-toggle
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
          @click.prevent="handleLinkClick('inicio', $event)"
          :class="isLinkActive('inicio') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="text-sm font-medium transition-colors"
        >
          Inicio
        </a>
        <a
          href="#coberturas"
          @click.prevent="handleLinkClick('coberturas', $event)"
          :class="isLinkActive('coberturas') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="text-sm font-medium transition-colors"
        >
          Coberturas
        </a>
        <a
          href="#nosotros"
          @click.prevent="handleLinkClick('nosotros', $event)"
          :class="isLinkActive('nosotros') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="text-sm font-medium transition-colors"
        >
          Nosotros
        </a>
        <a
          href="#como-funciona"
          @click.prevent="handleLinkClick('como-funciona', $event)"
          :class="isLinkActive('como-funciona') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="text-sm font-medium transition-colors"
        >
          Cómo Funciona
        </a>
        <a
          href="#ventajas"
          @click.prevent="handleLinkClick('ventajas', $event)"
          :class="isLinkActive('ventajas') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="text-sm font-medium transition-colors"
        >
          Ventajas
        </a>
      </div>

      <!-- Mobile Navigation -->
      <div v-if="isOpen" class="md:hidden flex flex-col w-full mt-8 pt-3 space-y-1 border-t border-white/10 flex-1" data-mobile-nav>
        <a
          href="#inicio"
          @click.prevent="handleLinkClick('inicio', $event, true)"
          :class="isLinkActive('inicio') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="block px-3 py-4 rounded-md text-lg font-medium transition-colors navbar-mobile-link"
        >
          Inicio
        </a>
        <a
          href="#coberturas"
          @click.prevent="handleLinkClick('coberturas', $event, true)"
          :class="isLinkActive('coberturas') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="block px-3 py-4 rounded-md text-lg font-medium transition-colors navbar-mobile-link"
        >
          Coberturas
        </a>
        <a
          href="#nosotros"
          @click.prevent="handleLinkClick('nosotros', $event, true)"
          :class="isLinkActive('nosotros') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="block px-3 py-4 rounded-md text-lg font-medium transition-colors navbar-mobile-link"
        >
          Nosotros
        </a>
        <a
          href="#como-funciona"
          @click.prevent="handleLinkClick('como-funciona', $event, true)"
          :class="isLinkActive('como-funciona') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="block px-3 py-4 rounded-md text-lg font-medium transition-colors navbar-mobile-link"
        >
          Cómo Funciona
        </a>
        <a
          href="#ventajas"
          @click.prevent="handleLinkClick('ventajas', $event, true)"
          :class="isLinkActive('ventajas') ? 'text-white font-bold' : 'text-white/80 hover:text-white'"
          class="block px-3 py-4 rounded-md text-lg font-medium transition-colors navbar-mobile-link"
        >
          Ventajas
        </a>

        <!-- CTA Button -->
        <div class="flex justify-start mt-auto pt-6 pb-3 w-full navbar-cta-button">
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
