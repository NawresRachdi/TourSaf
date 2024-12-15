<template>
  <div id="Popular_Destination" class="bg-gray-800 py-24 h-screen mt-20">
    <div class="mx-auto px-4 sm:px-6 lg:px-8">
      <h1 class="text-white text-4xl font-bold text-left mb-8">Popular Destination</h1>
      <div class="flex items-center overflow-x-auto scroll-m-0 custom-scroll">
        <div v-for="(country, index) in best.slice(0, 30)" :key="index" class="mx-2 my-2">
          <div class="w-72 h-96 border-2 border-white rounded-lg overflow-hidden shadow-lg p-1">
            <img :src="country.image" :alt="country.lieu_tourisme" class="w-full h-48 object-cover rounded-t-md" />
            <div class="p-2 flex flex-col justify-between h-40">
              <h4 class="text-white/80 text-lg font-bold">{{ country.nom }}</h4>
              <p class="text-gray-600 text-md mt-1">{{ country.description }}</p>
              <p class="text-gray-400 text-sm"><strong>Pays:</strong> {{ country.pays }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import best from '../../public/donnes/Lieuxtouristiques.json'
</script>

<style scoped>
.custom-scroll {
  overflow-x: scroll;
  width: 100%;
  padding-right: 10px;
}

.custom-scroll::-webkit-scrollbar {
  height: 6px;
}

.custom-scroll::-webkit-scrollbar-thumb {
  background: rgba(0, 0, 0, 0.3);
  border-radius: 10px;
}

.custom-scroll::-webkit-scrollbar-track {
  background: rgba(0, 0, 0, 0.1);
}
</style>
