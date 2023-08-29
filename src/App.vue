<template>
  <section>
    <div v-if="temas" id="">
      <div style="display: flex; flex-direction: column; gap: 35px; align-items: center;">
        <h1 style="color: rgb(253, 239, 214); font-size: 100px; font-family: fantasy; margin: 0;">Selecciona un tema</h1>
        <div style="display: flex; gap: 18px; flex-wrap: wrap; width: 380px; justify-content: center;">
          <button class="tema">Animales</button>
          <button class="tema">Frutas</button>
          <button class="tema">Ciudades</button>
          <button class="tema">Colores</button>
          <button class="tema">Marcas</button>
        </div>
      </div>
    </div>
    <div v-else id="inicio"> 
      <h1 style="color: rgb(253, 239, 214); font-size: 200px; font-family: fantasy; margin: 0;">AHORCADO</h1>
      <button id="jugar" @click="iniTemas">Jugar</button>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const temas = ref(false)

function iniTemas(){
  temas.value = true
} 

</script>

<style>

section{
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  min-height: 100vh;
  background: linear-gradient(rgb(250, 189, 74), rgb(34, 34, 150));
}

#inicio{
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 25px;
}

#jugar{
  width: 170px; 
  height: 40px; 
  font-size: 20px; 
  border: 0;
  border-radius: 5px;
  background-color: rgb(208, 208, 255); 
}

#jugar:hover{
  background: rgb(253, 239, 214);
  cursor: pointer;
}

.tema{
  width: 170px; 
  height: 40px; 
  font-size: 20px; 
  border: 0;
  border-radius: 5px;
  background-color: rgb(208, 208, 255); 
}

.tema:hover{
  background: rgb(253, 239, 214);
  cursor: pointer;
}

</style>