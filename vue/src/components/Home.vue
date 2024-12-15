<template>
    <div id="home" class="min-h-screen bg-gray-900 overflow-x-hidden">
      
     <Header/>
     <Tout_lieux/>
     
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
 
  import Header from './header.vue'
  import Tout_lieux from './tout_lieux.vue'
  
  const searchQuery = ref('')
  </script>