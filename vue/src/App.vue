<template>
  <div class="min-h-screen bg-gray-900 overflow-x-hidden">
    <Navbar/>
    <Home />
    <TheBest/>
    <Map/>
    <Footer />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Navbar from '../src/components/navbar.vue'
import Home from '../src/components/Home.vue'
import Footer from '../src/components/Footer.vue'
import Map from './components/map.vue'
import TheBest from './components/TheBest.vue'
const choixNav = ref('home')

const Continue = (active) => {
  choixNav.value = active
}
</script>
