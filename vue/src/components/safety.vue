<template>
    <div  class="relative h-screen">
      <!-- Section supérieure -->
      <div class="absolute inset-0 bg-gradient-to-b from-purple-900/90 to-gray-900 flex justify-between items-center pr-20">
        <div class="h-screen w-screen flex flex-col justify-center items-center mx-auto px-4 sm:px-6 lg:px-8 pt-32 z-30">
          <h1 class="text-6xl font-bold text-white mb-6  ">Safety First, Adventure Next!</h1>
          <p class="text-xl text-gray-300 mb-8">Discover the safest tourist destinations around the world.</p>
        </div>
        <img class="absolute inset-0 h-screen w-screen flex z-10 object-cover" src="/public/image/safet.jpg" alt="Safety Image" />
        <div class="absolute inset-0 h-screen w-screen flex z-20 bg-gradient-to-b from-gray-900/70   to-gray-900"></div>

      </div>
  
     
    </div>
     <!-- Section des lieux touristiques -->
      <div class="relative z-30  bg-gray-900 ">
        <div class="bg-gray-900 py-24 h-screen mt-20">
      <div class=" mx-auto px-4 sm:px-6 lg:px-8">
        <h1 class="text-white text-4xl font-bold text-left mb-8">Top 10 Safest Tourist Destinations in the World</h1>
        <div class="flex   items-center overflow-x-auto scroll-m-0 custom-scroll">
          <div v-for="(country, index) in best" :key="index" class="mx-2 my-2">
            <div class="w-72 h-96 border-2 border-white rounded-lg overflow-hidden shadow-lg p-1">
              <img :src="country.url_image" :alt="country.lieu_touristique" class="w-full h-48 object-cover rounded-t-md" />
              <div class="p-2 flex flex-col justify-between h-40">
                <h4 class="text-white/80 text-lg font-bold">{{ country.lieu_touristique}}</h4>
                <p class="text-gray-600 text-md mt-1">{{ country.information }}</p>
                <p class="text-gray-400 text-sm"><strong>Pays:</strong> {{ country.pays }}</p>
                <p class="text-gray-400 text-sm leading-relaxed">
                  <strong>Sécurité:</strong>{{  country.safety_percentage.toFixed(2) }}
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
        <div class="grid sm:grid-cols-2 items-center gap-8 font-[sans-serif] max-w-5xl max-sm:max-w-sm mx-auto p-4 bg-white my-20 rounded-lg">
      <div class="sm:h-[400px]">
        <img src="/public/image/safetybar.png" class="w-full h-full  object-contain" />
      </div>

      <div>
       <img src="/public/image/safety_pie_chart.png" alt="" class="w-full h-full  object-contain">

      </div>
    </div>
    <Map/>
      </div>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue';
  import Map from '../components/map.vue'
  import best from '../../public/donnes/top_safety.json'
  
  </script>
  
  <style scoped>
  .custom-scroll {
    scrollbar-width: thin;
    scrollbar-color: #4a5568 transparent;
  }
  
  .custom-scroll::-webkit-scrollbar {
    height: 8px;
  }
  
  .custom-scroll::-webkit-scrollbar-thumb {
    background-color: #4a5568;
    border-radius: 4px;
  }
  
  .custom-scroll::-webkit-scrollbar-track {
    background: transparent;
  }
 
.map-container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  border-radius: 8px;
  overflow: hidden;
}
</style>
  