<script setup>
import Header from './components/Header.vue'
import Navbar from './components/Navbar.vue'
import HowItWorks from './components/HowItWorks.vue'
import Coberturas from './components/Coberturas.vue'
import AboutAplick from './components/AboutAplick.vue'
import PorqueElegirnos from './components/PorqueElegirnos.vue'
import Footer from './components/Footer.vue'
</script>

<template>
  <div class="bg-black">
    <Navbar />
    <section id="inicio">
      <Header />
    </section>
    <section id="coberturas" class="scroll-mt-24">
      <Coberturas />
    </section>
    <section id="nosotros" class="scroll-mt-24">
      <AboutAplick />
    </section>
    <section id="como-funciona" class="scroll-mt-15">
      <HowItWorks />
    </section>
    <section id="ventajas" class="scroll-mt-24">
      <PorqueElegirnos />
    </section>
    <Footer />
  </div>
</template>

<style scoped>

</style>
