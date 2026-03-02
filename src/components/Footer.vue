<script setup>
const currentYear = new Date().getFullYear()
</script>

<template>
  <footer class="w-full bg-black mt-12 border-t border-white/10">
    <div class="mx-4 sm:mx-6 lg:mx-8 py-12">
      <div class="w-full">
        <!-- Footer Container -->
        <div class="rounded-3xl overflow-hidden" style="background: linear-gradient(135deg, rgba(25, 93, 76, 0.1) 0%, rgba(143, 207, 154, 0.05) 50%, rgba(26, 26, 26, 1) 100%);">
          <div class="px-6 sm:px-12 lg:px-16 py-12 sm:py-16">
            <!-- Footer Content Grid -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8 mb-12">
              <!-- Logo Section -->
              <div class="flex flex-col items-start">
                <img src="/public/Logo-Aplick-Sub-Titulo.png" alt="Logo Aplick" class="h-14 w-auto mb-4">
                <p class="text-white/60 text-sm leading-relaxed">
                  La plataforma digital que simplifica la cotización de seguros mediante inteligencia artificial.
                </p>
              </div>

              <!-- Quick Links -->
              <div>
                <h4 class="text-[#f7f7ad] font-bold mb-4">Enlaces</h4>
                <ul class="space-y-2">
                  <li>
                    <a href="#" class="text-white/60 hover:text-white text-sm transition-colors">
                      Inicio
                    </a>
                  </li>
                  <li>
                    <a href="#" class="text-white/60 hover:text-white text-sm transition-colors">
                      Coberturas
                    </a>
                  </li>
                  <li>
                    <a href="#" class="text-white/60 hover:text-white text-sm transition-colors">
                      Sobre Nosotros
                    </a>
                  </li>
                  <li>
                    <a href="#" class="text-white/60 hover:text-white text-sm transition-colors">
                      Contacto
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

            <!-- Divider -->
            <div class="h-px bg-gradient-to-r from-transparent via-white/20 to-transparent mb-8"></div>

            <!-- Copyright -->
            <div class="text-center">
              <p class="text-white/60 text-sm">
                © {{ currentYear }} Aplick. Todos los derechos reservados.
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<style scoped>
</style>
