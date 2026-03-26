<script setup>
const currentYear = new Date().getFullYear()
</script>

<template>
  <footer class="w-full relative" style="background: linear-gradient(135deg, rgba(25, 93, 76, 0.1) 0%, rgba(143, 207, 154, 0.05) 50%, rgba(26, 26, 26, 1) 100%);">
    <!-- Top fade from previous section -->
    <div class="absolute top-0 left-0 right-0 h-32 bg-gradient-to-b from-black to-transparent pointer-events-none z-10"></div>

    <div class="w-full px-6 sm:px-12 lg:px-16 py-16 sm:py-20 relative z-20 mt-12">
      <!-- Footer Content Grid -->
      <div class="flex flex-col md:flex md:flex-row md:items-start gap-8 md:gap-16 mb-12">
        <!-- Logo Section -->
        <div class="flex flex-col items-start shrink-0">
          <img src="/Logo-Aplick-Sub-Titulo.png" alt="Logo Aplick" class="h-14 w-auto mb-4">
          <p class="text-white/60 text-sm leading-relaxed max-w-xs">
            La plataforma digital que simplifica la cotización de seguros mediante inteligencia artificial.
          </p>
        </div>

        <!-- Links Container (Mobile and Desktop: flex row centered) -->
        <div class="flex flex-row gap-16 md:gap-32 flex-1 md:justify-center">
          <!-- Quick Links -->
          <div>
            <h4 class="text-[#f7f7ad] font-bold mb-4">Enlaces</h4>
            <ul class="space-y-2">
              <li>
                <a href="#coberturas" class="text-white/60 hover:text-white text-sm transition-colors">
                  Coberturas
                </a>
              </li>
              <li>
                <a href="#nosotros" class="text-white/60 hover:text-white text-sm transition-colors">
                  Nosotros
                </a>
              </li>
              <li>
                <a href="#como-funciona" class="text-white/60 hover:text-white text-sm transition-colors">
                  Cómo Funciona
                </a>
              </li>
              <li>
                <a href="#ventajas" class="text-white/60 hover:text-white text-sm transition-colors">
                  Ventajas
                </a>
              </li>
            </ul>
          </div>

          <!-- Legal Links -->
          <div>
            <h4 class="text-[#f7f7ad] font-bold mb-4">Legal</h4>
            <ul class="space-y-2">
              <li>
                <a href="#" class="text-white/60 hover:text-white text-sm transition-colors">
                  Términos y Condiciones
                </a>
              </li>
              <li>
                <a href="#" class="text-white/60 hover:text-white text-sm transition-colors">
                  Política de Privacidad
                </a>
              </li>
              <li>
                <a href="#" class="text-white/60 hover:text-white text-sm transition-colors">
                  Cookies
                </a>
              </li>
            </ul>
          </div>
        </div>
      </div>

      <!-- Divider -->
      <div class="h-px bg-gradient-to-r from-transparent via-white/20 to-transparent mb-8"></div>

      <!-- Copyright -->
        <div class="text-center flex flex-col md:flex-row items-center justify-center gap-4">
          <p class="text-white/60 text-sm">
            © {{ currentYear }} Aplick. Todos los derechos reservados.
          </p>
          
          <!-- Logos Container -->
          <div class="flex flex-row items-center justify-center gap-4">
            <a 
              href="https://web.seiminteractive.io/" 
              target="_blank" 
              rel="noopener noreferrer"
              class="transition-opacity hover:opacity-80"
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
              class="transition-opacity hover:opacity-80"
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
