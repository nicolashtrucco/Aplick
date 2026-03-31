<script setup lang="ts">
import gsap from 'gsap'
import { onMounted } from 'vue'

const currentYear = new Date().getFullYear()

onMounted(() => {
  // Use setTimeout to ensure DOM is ready
  setTimeout(() => {
    setupFooterObserver()
  }, 100)
})

const setupFooterObserver = () => {
  const footer = document.querySelector('footer')
  if (!footer) return

  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          animateFooter()
          observer.unobserve(footer)
        }
      })
    },
    { threshold: 0.2 }
  )

  observer.observe(footer)
}

const animateFooter = () => {
  // Set initial state for all elements
  gsap.set('.footer-logo', { opacity: 1 })
  gsap.set('.footer-description', { opacity: 1 })
  gsap.set('.footer-links-section', { opacity: 1 })
  gsap.set('.footer-link-column', { opacity: 1 })
  gsap.set('.footer-divider', { opacity: 1 })
  gsap.set('.footer-copyright', { opacity: 1 })
  gsap.set('.footer-logo-item', { opacity: 1 })

  // Animate logo section
  gsap.from('.footer-logo', {
    opacity: 0,
    x: -30,
    duration: 0.6,
    ease: 'power2.out',
  })

  // Animate logo description
  gsap.from('.footer-description', {
    opacity: 0,
    x: -20,
    duration: 0.6,
    delay: 0.1,
    ease: 'power2.out',
  })

  // Animate links section
  gsap.from('.footer-links-section', {
    opacity: 0,
    y: 30,
    duration: 0.6,
    delay: 0.2,
    ease: 'power2.out',
  })

  // Animate each link column with stagger
  const linkColumns = document.querySelectorAll('.footer-link-column') as NodeListOf<HTMLElement>
  gsap.from(linkColumns, {
    opacity: 0,
    y: 20,
    duration: 0.5,
    stagger: 0.1,
    delay: 0.3,
    ease: 'power2.out',
  })

  // Animate divider
  gsap.from('.footer-divider', {
    scaleX: 0,
    opacity: 0,
    duration: 0.7,
    delay: 0.4,
    ease: 'power2.out',
  })

  // Animate copyright section
  gsap.from('.footer-copyright', {
    opacity: 0,
    y: 20,
    duration: 0.6,
    delay: 0.5,
    ease: 'power2.out',
  })

  // Animate logos with stagger
  const logos = document.querySelectorAll('.footer-logo-item') as NodeListOf<HTMLElement>
  gsap.from(logos, {
    opacity: 0,
    scale: 0.8,
    duration: 0.5,
    stagger: 0.1,
    delay: 0.6,
    ease: 'back.out',
  })

  // Add hover effect to links
  const links = document.querySelectorAll('.footer-link')
  links.forEach((link) => {
    link.addEventListener('mouseenter', () => {
      gsap.to(link, { x: 5, duration: 0.3, ease: 'power2.out' })
    })
    link.addEventListener('mouseleave', () => {
      gsap.to(link, { x: 0, duration: 0.3, ease: 'power2.out' })
    })
  })
}
</script>

<template>
  <footer class="w-full relative" data-footer-section style="background: linear-gradient(135deg, rgba(25, 93, 76, 0.1) 0%, rgba(143, 207, 154, 0.05) 50%, rgba(26, 26, 26, 1) 100%);">
    <!-- Top fade from previous section -->
    <div class="absolute top-0 left-0 right-0 h-32 bg-gradient-to-b from-black to-transparent pointer-events-none z-10"></div>

    <div class="w-full px-6 sm:px-12 lg:px-16 py-16 sm:py-20 relative z-20 mt-12">
      <!-- Footer Content Grid -->
      <div class="flex flex-col md:flex md:flex-row md:items-start gap-8 md:gap-16 mb-12">
        <!-- Logo Section -->
        <div class="footer-logo flex flex-col items-start shrink-0">
          <img src="/Logo-Aplick-Sub-Titulo.png" alt="Logo Aplick" class="h-14 w-auto mb-4">
          <p class="footer-description text-white/60 text-sm leading-relaxed max-w-xs">
            La plataforma digital que simplifica la cotización de seguros mediante inteligencia artificial.
          </p>
        </div>

        <!-- Links Container (Mobile and Desktop: flex row centered) -->
        <div class="footer-links-section flex flex-row gap-16 md:gap-32 flex-1 md:justify-center">
          <!-- Quick Links -->
          <div class="footer-link-column">
            <h4 class="text-[#f7f7ad] font-bold mb-4">Enlaces</h4>
            <ul class="space-y-2">
              <li>
                <a href="#coberturas" class="footer-link text-white/60 hover:text-white text-sm transition-colors">
                  Coberturas
                </a>
              </li>
              <li>
                <a href="#nosotros" class="footer-link text-white/60 hover:text-white text-sm transition-colors">
                  Nosotros
                </a>
              </li>
              <li>
                <a href="#como-funciona" class="footer-link text-white/60 hover:text-white text-sm transition-colors">
                  Cómo Funciona
                </a>
              </li>
              <li>
                <a href="#ventajas" class="footer-link text-white/60 hover:text-white text-sm transition-colors">
                  Ventajas
                </a>
              </li>
            </ul>
          </div>

          <!-- Legal Links -->
          <div class="footer-link-column">
            <h4 class="text-[#f7f7ad] font-bold mb-4">Legal</h4>
            <ul class="space-y-2">
              <li>
                <a href="#" class="footer-link text-white/60 hover:text-white text-sm transition-colors">
                  Términos y Condiciones
                </a>
              </li>
              <li>
                <a href="#" class="footer-link text-white/60 hover:text-white text-sm transition-colors">
                  Política de Privacidad
                </a>
              </li>
              <li>
                <a href="#" class="footer-link text-white/60 hover:text-white text-sm transition-colors">
                  Cookies
                </a>
              </li>
            </ul>
          </div>
        </div>
      </div>

      <!-- Divider -->
      <div class="footer-divider h-px bg-gradient-to-r from-transparent via-white/20 to-transparent mb-8"></div>

      <!-- Copyright -->
        <div class="footer-copyright text-center flex flex-col md:flex-row items-center justify-center gap-4">
          <p class="text-white/60 text-sm">
            © {{ currentYear }} Aplick. Todos los derechos reservados.
          </p>
          
          <!-- Logos Container -->
          <div class="flex flex-row items-center justify-center gap-4">
            <a 
              href="https://web.seiminteractive.io/" 
              target="_blank" 
              rel="noopener noreferrer"
              class="footer-logo-item transition-opacity hover:opacity-80"
            >
              <img 
                src="/SeimFooterBlanco.png" 
                alt="Seim Interactive" 
                class="h-6 w-auto"
              >
            </a>
            <a 
              href="https://byloa.agency/" 
              target="_blank" 
              rel="noopener noreferrer"
              class="footer-logo-item transition-opacity hover:opacity-80"
            >
              <img 
                src="/logotipos_logotipodescriptorv2 negativo.png" 
                alt="Byloa Agency" 
                class="h-6 w-auto"
              >
            </a>
          </div>
        </div>
    </div>
  </footer>
</template>

<style scoped>
</style>
