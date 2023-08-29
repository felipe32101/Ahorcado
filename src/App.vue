<template>
  <section>
    <h1 style="color: rgb(253, 239, 214); font-size: 200px; font-family: fantasy; margin: 0;">AHORCADO</h1>
    <button id="jugar">Jugar</button>
  </section>
</template>

<script setup>

</script>

<style>

section{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  min-height: 100vh;
  gap: 50px;
  background: linear-gradient(rgb(250, 189, 74), rgb(34, 34, 150));
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

</style>