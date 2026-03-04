<script setup>
import Header from './components/Header.vue'
import HowItWorks from './components/HowItWorks.vue'
import Coberturas from './components/Coberturas.vue'
import AboutAplick from './components/AboutAplick.vue'
import PorqueElegirnos from './components/PorqueElegirnos.vue'
import Footer from './components/Footer.vue'
</script>

<template>
  <div class="bg-black">
    <Header />
    <Coberturas />
    <div class="mt-4 mx-4 sm:mx-6 lg:mx-8">
      <AboutAplick />
      <HowItWorks />
      <PorqueElegirnos />
    </div>
    <Footer />
  </div>
</template>

<style scoped>

</style>
