<template>
    <div class="w-screen bg-gray-900 pb-10">
        <h1 class="text-3xl text-white w-screen text-center pt-10">Map of security in the world</h1>
        <div class="h-14 w-screen bg-gray-900 relative z-40 -mb-14"></div>
       <div class="map-container bg-gray-200 relative z-10 ">
    <iframe
      src="https://fr.numbeo.com/prix-de-l%27immobilier/carte-des-classements-actuels"
      frameborder="0"
      width="100%"
      height="600"
      allowfullscreen
    ></iframe>
  </div> 
    </div>
    
  </template>

  
  <style scoped>
 
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
  