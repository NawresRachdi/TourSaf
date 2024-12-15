<template>
  <div class="relative z-40 -mt-48">
    <div class="w-screen flex justify-center">
      <div class="bg-white w-1/2 h-16 flex px-1 py-1 rounded-full border border-blue-500 shadow-md shadow-blue-500/80 overflow-hidden mx-auto font-[sans-serif]">
        <input 
          v-model="searchText" 
          type="text" 
          placeholder="Search Something..." 
          class="w-full outline-none bg-white pl-4 text-sm" 
        />
        <button 
          v-if="!searchText" 
          type="button" 
          class="bg-blue-600 hover:bg-blue-700 transition-all text-white text-sm rounded-full px-5 py-2.5">
          Search
        </button>
        <button 
          v-if="searchText" 
          @click="searchText=''" 
          type="button" 
          class="bg-blue-100 hover:bg-blue-200 transition-all text-blue-700 text-sm rounded-full px-5 py-2.5">
          Delete
        </button>
      </div>
    </div>

    <div class="w-screen font-[sans-serif] my-4 bg-gray-900 -mt-9 pt-20">
      <div class="w-11/12 mx-auto">
        <div class="max-w-2xl mx-auto text-center">
          <h2 class="text-gray-500 text-3xl font-bold">Global Insights</h2>
          <p class="text-gray-600 text-sm mt-4 leading-relaxed">
            Get the latest updates on tourist attractions and safety worldwide.
          </p>
        </div>

        <div v-if="filteredData.length" class="flex flex-wrap justify-center items-center custom-scroll">
          <div 
            v-for="(country, index) in filteredData" 
            :key="index" 
            class="mx-2 my-2">
            <div class="w-72 h-96 border-2 border-white rounded-lg overflow-hidden shadow-lg p-1">
              <img 
                :src="country.urlimage" 
                :alt="country.nom" 
                class="w-full h-48 object-cover rounded-t-md" 
              />
              <div class="p-2 flex flex-col justify-between h-20">
                <h4 class="text-white/80 text-lg font-bold">{{ country.nom }}</h4>
                <p class="text-gray-600 text-md mt-1">{{ country.description }}</p>
                <p class="text-gray-400 text-sm leading-relaxed">
                  <strong>Pays:</strong> {{ country.pays }}
                </p>
                <p class="text-gray-400 text-sm leading-relaxed">
                  <strong>Sécurité:</strong>
                  {{ country.safety !== "NaN" ? country.safety + "%" : "Non disponible" }}
                </p>
              </div>
            </div>
          </div>
        </div>
        <p v-else class="text-white text-center mt-10">Aucun résultat trouvé.</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";
import touristData from "../../public/donnes/structured_result_final.json";

const searchText = ref("");

// Filtrage des données
const filteredData = computed(() => {
  if (!Array.isArray(touristData)) return [];
  return touristData.filter((country) => {
    const matchesText = searchText.value
      ? country.nom?.toLowerCase().includes(searchText.value.toLowerCase())
      : true;
    return matchesText;
  });
});
</script>

<style scoped>
/* Style personnalisé pour le défilement */
.custom-scroll {
  overflow-y: auto;
  max-height: 100vh; /* Limite la hauteur de la zone défilante */
}

/* Ajustement de la barre de défilement */
.custom-scroll::-webkit-scrollbar {
  width: 8px;
}

.custom-scroll::-webkit-scrollbar-thumb {
  background: rgba(0, 0, 0, 0.3);
  border-radius: 10px;
}

.custom-scroll::-webkit-scrollbar-track {
  background: rgba(0, 0, 0, 0.1);
}
</style>
