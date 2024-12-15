<template>
  <nav class="bg-gray-600/30 backdrop-blur-sm fixed w-full z-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-16">
        <!-- Logo Section -->
        <div class="flex items-center">
          <a href="#" class="text-white text-2xl font-bold">
            <span class="text-3xl text-blue-700">T</span>our
            <span class="text-2xl text-blue-700">S</span>afe
          </a>
        </div>

        <!-- Navigation Links -->
        <div class="flex items-center space-x-8 text-lg font-semibold">
          <!-- Home Link -->
          <a 
            href="#home" 
            :class="{
              'text-blue-600 border-b-2 border-blue-700 pb-1': active === 'H',
              'text-white hover:text-gray-300 pb-1': active !== 'H'
            }" 
            @click="setActive('H', 'home')"
          >
            Home
          </a>

          <!-- Popular Destination Link -->
          <a 
            href="#Popular_Destination" 
            :class="{
              'text-blue-600 border-b-2 border-blue-700 pb-1': active === 'S',
              'text-white hover:text-gray-300 pb-1': active !== 'S'
            }" 
            @click="setActive('S', 'safety')"
          >
            Popular Destination
          </a>

          <!-- Sign Up Button -->
          <div
            href="#" 
            @click="ouverte = true" 
            class="text-white bg-blue-800 text-xl px-4 py-2 rounded-lg cursor-pointer"
          >
            Sign Up
        </div>
        </div>
      </div>
    </div> 
    
  </nav>
<div v-if="ouverte" class="h-screen w-screen z-50 fixed">
    <sign  @close="ouverte=false"/>
</div>
 
</template>

<script setup>
import { ref, defineEmits } from 'vue';
import sign from './sign.vue'
const emit = defineEmits(['activeChange']);
const active = ref('H'); // Définit la section active par défaut
const ouverte = ref(false); // Contrôle l'affichage du composant Sign

// Fonction pour changer l'état de la section active
const setActive = (newActive, section) => {
  active.value = newActive;
  emit('activeChange', section);
};
</script>

<style scoped>
</style>
