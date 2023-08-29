<template>
  <section>
    <div v-if="temas" id="">
      <div v-if="!temaSeleccionado" class="div" style="display: flex; display: flex;flex-direction: column;align-items: center; gap: 35px;">
        <h1 style="color: rgb(253, 239, 214); font-size: 100px; font-family: fantasy; margin: 0;">Selecciona un tema</h1>
        <div style="display: flex; gap: 18px; flex-wrap: wrap; width: 380px; justify-content: center;">
          <button class="tema" @click="seleccionarTema('Animales')">Animales</button>
          <button class="tema" @click="seleccionarTema('Frutas')">Frutas</button>
          <button class="tema" @click="seleccionarTema('Ciudades')">Ciudades</button>
          <button class="tema" @click="seleccionarTema('Colores')">Colores</button>
          <button class="tema" @click="seleccionarTema('Marcas')">Marcas</button>
        </div>
      </div>
      <div v-else style="display: flex; flex-direction: column; gap: 35px;">
  <h1 style="color: rgb(253, 239, 214); font-size: 100px; font-family: fantasy; margin: 0;">Selecciona una dificultad</h1>
  <div style="display: flex; gap: 18px; flex-wrap: wrap; justify-content: center; display: flex; flex-direction: column; align-items: center;">
    <button class="tema" @click="seleccionarDificultad('Facil')">Facil</button>
    <button class="tema" @click="seleccionarDificultad('Medio')">Medio</button>
    <button class="tema" @click="seleccionarDificultad('Dificil')">Dificil</button>
    <!-- Agregar imagen después de seleccionar la dificultad -->
    <img v-if="dificultadSeleccionada" :src="img" alt="Imagen relacionada al tema y dificultad">
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
import img from '/src/2.jpg'

const temas = ref(false)
const temaSeleccionado = ref(null);
const dificultadSeleccionada = ref(null);

function iniTemas(){
  temas.value = true;
  temaSeleccionado.value = null;
}

function seleccionarTema(tema){
  temaSeleccionado.value = tema;
} 
function seleccionarDificultad(dificultad) {
  dificultadSeleccionada.value = dificultad;
}
</script>

<style>
img {
  width: 200px;
  height: 200px;
}
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
