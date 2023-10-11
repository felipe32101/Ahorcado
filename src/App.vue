<template>
  <section>
    <div v-if="temas" id="">
      <div v-if="!temaSeleccionado" class="div"
        style="display: flex; display: flex;flex-direction: column;align-items: center; gap: 35px;">
        <h1 style="color: rgb(253, 239, 214); font-size: 100px; font-family: fantasy; margin: 0;">Selecciona un tema</h1>
        <div style="display: flex; gap: 18px; flex-wrap: wrap; width: 380px; justify-content: center;">
          <button class="tema" @click="seleccionarTema('Animales')">Animales</button>
          <button class="tema" @click="seleccionarTema('Frutas')">Frutas</button>
          <button class="tema" @click="seleccionarTema('Ciudades')">Ciudades</button>
          <button class="tema" @click="seleccionarTema('Colores')">Colores</button>
          <button class="tema" @click="seleccionarTema('Marcas')">Marcas de ropa</button>
        </div>
      </div>
      <div v-else style="display: flex; flex-direction: column; gap: 35px;">
        <h1 style="color: rgb(253, 239, 214); font-size: 100px; font-family: fantasy; margin: 0;"
          v-if="!dificultadSeleccionada">Selecciona una
          dificultad</h1>
        <div
          style="display: flex; gap: 18px; flex-wrap: wrap; justify-content: center; display: flex; flex-direction: column; align-items: center;">
          <button class="tema" @click="seleccionarDificultad('Facil')" v-if="!dificultadSeleccionada">Facil</button>
          <button class="tema" @click="seleccionarDificultad('Medio')" v-if="!dificultadSeleccionada">Medio</button>
          <button class="tema" @click="seleccionarDificultad('Dificil')" v-if="!dificultadSeleccionada">Dificil</button>
          <div style="display: flex;"
            v-if="dificultadSeleccionada && temaSeleccionado === 'Animales' && dificultadSeleccionada === 'Facil'">
            <div class="vif">
              <img :src="imagenOportunidad">
              <div v-if="palabraAdivinada">
                <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
              </div>
              <div v-if="palabraIncorrecta">
                <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
              </div>
              <div style="display: flex; flex-direction: row; width: 100%; gap: 10%; justify-content: center;">
                <div class="letras-adivinadas">
                  <span v-for="letra in palabraActual">{{ letrasAdivinadas.includes(letra) ? letra : '_' }}</span>
                </div>
              </div>
              <div class="letras">
                <button v-for="letra in alfabeto" :key="letra" @click="adivinarLetra(letra)"
                  :disabled="letrasAdivinadas.includes(letra) || letrasIncorrectas.includes(letra)">
                  {{ letra }}
                </button>
              </div>
            </div>
          </div>
          <div style="display: flex;"
            v-if="dificultadSeleccionada && temaSeleccionado === 'Animales' && dificultadSeleccionada === 'Medio'">
            <div class="vif">
              <div class="vif">
                <img :src="imagenOportunidad">
                <div v-if="palabraAdivinada">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div v-if="palabraIncorrecta">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div style="display: flex; flex-direction: row; width: 100%; gap: 10%; justify-content: center;">
                  <div class="letras-adivinadas">
                    <span v-for="letra in palabraActual">{{ letrasAdivinadas.includes(letra) ? letra : '_' }}</span>
                  </div>
                </div>
                <div class="letras">
                  <button v-for="letra in alfabeto" :key="letra" @click="adivinarLetra(letra)"
                    :disabled="letrasAdivinadas.includes(letra) || letrasIncorrectas.includes(letra)">
                    {{ letra }}
                  </button>
                </div>
              </div>
            </div>
          </div>
          <div style="display: flex;"
            v-if="dificultadSeleccionada && temaSeleccionado === 'Animales' && dificultadSeleccionada === 'Dificil'">
            <div class="vif">
              <div class="vif">
                <img :src="imagenOportunidad">
                <div v-if="palabraAdivinada">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div v-if="palabraIncorrecta">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div style="display: flex; flex-direction: row; width: 100%; gap: 10%; justify-content: center;">
                  <div class="letras-adivinadas">
                    <span v-for="letra in palabraActual">{{ letrasAdivinadas.includes(letra) ? letra : '_' }}</span>
                  </div>
                </div>
                <div class="letras">
                  <button v-for="letra in alfabeto" :key="letra" @click="adivinarLetra(letra)"
                    :disabled="letrasAdivinadas.includes(letra) || letrasIncorrectas.includes(letra)">
                    {{ letra }}
                  </button>
                </div>
              </div>
            </div>
          </div>
          <div style="display: flex;"
            v-if="dificultadSeleccionada && temaSeleccionado === 'Frutas' && dificultadSeleccionada === 'Facil'">
            <div class="vif">
              <img :src="imagenOportunidad">
              <div v-if="palabraAdivinada">
                <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
              </div>
              <div v-if="palabraIncorrecta">
                <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
              </div>
              <div style="display: flex; flex-direction: row; width: 100%; gap: 10%; justify-content: center;">
                <div class="letras-adivinadas">
                  <span v-for="letra in palabraActual">{{ letrasAdivinadas.includes(letra) ? letra : '_' }}</span>
                </div>
              </div>
              <div class="letras">
                <button v-for="letra in alfabeto" :key="letra" @click="adivinarLetra(letra)"
                  :disabled="letrasAdivinadas.includes(letra) || letrasIncorrectas.includes(letra)">
                  {{ letra }}
                </button>
              </div>
            </div>
          </div>
          <div style="display: flex;"
            v-if="dificultadSeleccionada && temaSeleccionado === 'Frutas' && dificultadSeleccionada === 'Medio'">
            <div class="vif">
              <div class="vif">
                <img :src="imagenOportunidad">
                <div v-if="palabraAdivinada">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div v-if="palabraIncorrecta">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div style="display: flex; flex-direction: row; width: 100%; gap: 10%; justify-content: center;">
                  <div class="letras-adivinadas">
                    <span v-for="letra in palabraActual">{{ letrasAdivinadas.includes(letra) ? letra : '_' }}</span>
                  </div>
                </div>
                <div class="letras">
                  <button v-for="letra in alfabeto" :key="letra" @click="adivinarLetra(letra)"
                    :disabled="letrasAdivinadas.includes(letra) || letrasIncorrectas.includes(letra)">
                    {{ letra }}
                  </button>
                </div>
              </div>
            </div>
          </div>
          <div style="display: flex;"
            v-if="dificultadSeleccionada && temaSeleccionado === 'Frutas' && dificultadSeleccionada === 'Dificil'">
            <div class="vif">
              <div class="vif">
                <img :src="imagenOportunidad">
                <div v-if="palabraAdivinada">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div v-if="palabraIncorrecta">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div style="display: flex; flex-direction: row; width: 100%; gap: 10%; justify-content: center;">
                  <div class="letras-adivinadas">
                    <span v-for="letra in palabraActual">{{ letrasAdivinadas.includes(letra) ? letra : '_' }}</span>
                  </div>
                </div>
                <div class="letras">
                  <button v-for="letra in alfabeto" :key="letra" @click="adivinarLetra(letra)"
                    :disabled="letrasAdivinadas.includes(letra) || letrasIncorrectas.includes(letra)">
                    {{ letra }}
                  </button>
                </div>
              </div>
            </div>
          </div>
          <div style="display: flex;"
            v-if="dificultadSeleccionada && temaSeleccionado === 'Ciudades' && dificultadSeleccionada === 'Facil'">
            <div class="vif">
              <img :src="imagenOportunidad">
              <div v-if="palabraAdivinada">
                <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
              </div>
              <div v-if="palabraIncorrecta">
                <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
              </div>
              <div style="display: flex; flex-direction: row; width: 100%; gap: 10%; justify-content: center;">
                <div class="letras-adivinadas">
                  <span v-for="letra in palabraActual">{{ letrasAdivinadas.includes(letra) ? letra : '_' }}</span>
                </div>
              </div>
              <div class="letras">
                <button v-for="letra in alfabeto" :key="letra" @click="adivinarLetra(letra)"
                  :disabled="letrasAdivinadas.includes(letra) || letrasIncorrectas.includes(letra)">
                  {{ letra }}
                </button>
              </div>
            </div>
          </div>
          <div style="display: flex;"
            v-if="dificultadSeleccionada && temaSeleccionado === 'Ciudades' && dificultadSeleccionada === 'Medio'">
            <div class="vif">
              <div class="vif">
                <img :src="imagenOportunidad">
                <div v-if="palabraAdivinada">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div v-if="palabraIncorrecta">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div style="display: flex; flex-direction: row; width: 100%; gap: 10%; justify-content: center;">
                  <div class="letras-adivinadas">
                    <span v-for="letra in palabraActual">{{ letrasAdivinadas.includes(letra) ? letra : '_' }}</span>
                  </div>
                </div>
                <div class="letras">
                  <button v-for="letra in alfabeto" :key="letra" @click="adivinarLetra(letra)"
                    :disabled="letrasAdivinadas.includes(letra) || letrasIncorrectas.includes(letra)">
                    {{ letra }}
                  </button>
                </div>
              </div>
            </div>
          </div>
          <div style="display: flex;"
            v-if="dificultadSeleccionada && temaSeleccionado === 'Ciudades' && dificultadSeleccionada === 'Dificil'">
            <div class="vif">
              <div class="vif">
                <img :src="imagenOportunidad">
                <div v-if="palabraAdivinada">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div v-if="palabraIncorrecta">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div style="display: flex; flex-direction: row; width: 100%; gap: 10%; justify-content: center;">
                  <div class="letras-adivinadas">
                    <span v-for="letra in palabraActual">{{ letrasAdivinadas.includes(letra) ? letra : '_' }}</span>
                  </div>
                </div>
                <div class="letras">
                  <button v-for="letra in alfabeto" :key="letra" @click="adivinarLetra(letra)"
                    :disabled="letrasAdivinadas.includes(letra) || letrasIncorrectas.includes(letra)">
                    {{ letra }}
                  </button>
                </div>
              </div>
            </div>
          </div>
          <div style="display: flex;"
            v-if="dificultadSeleccionada && temaSeleccionado === 'Colores' && dificultadSeleccionada === 'Facil'">
            <div class="vif">
              <img :src="imagenOportunidad">
              <div v-if="palabraAdivinada">
                <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
              </div>
              <div v-if="palabraIncorrecta">
                <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
              </div>
              <div style="display: flex; flex-direction: row; width: 100%; gap: 10%; justify-content: center;">
                <div class="letras-adivinadas">
                  <span v-for="letra in palabraActual">{{ letrasAdivinadas.includes(letra) ? letra : '_' }}</span>
                </div>
              </div>
              <div class="letras">
                <button v-for="letra in alfabeto" :key="letra" @click="adivinarLetra(letra)"
                  :disabled="letrasAdivinadas.includes(letra) || letrasIncorrectas.includes(letra)">
                  {{ letra }}
                </button>
              </div>
            </div>
          </div>
          <div style="display: flex;"
            v-if="dificultadSeleccionada && temaSeleccionado === 'Colores' && dificultadSeleccionada === 'Medio'">
            <div class="vif">
              <div class="vif">
                <img :src="imagenOportunidad">
                <div v-if="palabraAdivinada">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div v-if="palabraIncorrecta">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div style="display: flex; flex-direction: row; width: 100%; gap: 10%; justify-content: center;">
                  <div class="letras-adivinadas">
                    <span v-for="letra in palabraActual">{{ letrasAdivinadas.includes(letra) ? letra : '_' }}</span>
                  </div>
                </div>
                <div class="letras">
                  <button v-for="letra in alfabeto" :key="letra" @click="adivinarLetra(letra)"
                    :disabled="letrasAdivinadas.includes(letra) || letrasIncorrectas.includes(letra)">
                    {{ letra }}
                  </button>
                </div>
              </div>
            </div>
          </div>
          <div style="display: flex;"
            v-if="dificultadSeleccionada && temaSeleccionado === 'Colores' && dificultadSeleccionada === 'Dificil'">
            <div class="vif">
              <div class="vif">
                <img :src="imagenOportunidad">
                <div v-if="palabraAdivinada">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div v-if="palabraIncorrecta">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div style="display: flex; flex-direction: row; width: 100%; gap: 10%; justify-content: center;">
                  <div class="letras-adivinadas">
                    <span v-for="letra in palabraActual">{{ letrasAdivinadas.includes(letra) ? letra : '_' }}</span>
                  </div>
                </div>
                <div class="letras">
                  <button v-for="letra in alfabeto" :key="letra" @click="adivinarLetra(letra)"
                    :disabled="letrasAdivinadas.includes(letra) || letrasIncorrectas.includes(letra)">
                    {{ letra }}
                  </button>
                </div>
              </div>
            </div>
          </div>
          <div style="display: flex;"
            v-if="dificultadSeleccionada && temaSeleccionado === 'Marcas' && dificultadSeleccionada === 'Facil'">
            <div class="vif">
              <img :src="imagenOportunidad">
              <div v-if="palabraAdivinada">
                <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
              </div>
              <div v-if="palabraIncorrecta">
                <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
              </div>
              <div style="display: flex; flex-direction: row; width: 100%; gap: 10%; justify-content: center;">
                <div class="letras-adivinadas">
                  <span v-for="letra in palabraActual">{{ letrasAdivinadas.includes(letra) ? letra : '_' }}</span>
                </div>
              </div>
              <div class="letras">
                <button v-for="letra in alfabeto" :key="letra" @click="adivinarLetra(letra)"
                  :disabled="letrasAdivinadas.includes(letra) || letrasIncorrectas.includes(letra)">
                  {{ letra }}
                </button>
              </div>
            </div>
          </div>
          <div style="display: flex;"
            v-if="dificultadSeleccionada && temaSeleccionado === 'Marcas' && dificultadSeleccionada === 'Medio'">
            <div class="vif">
              <div class="vif">
                <img :src="imagenOportunidad">
                <div v-if="palabraAdivinada">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div v-if="palabraIncorrecta">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div style="display: flex; flex-direction: row; width: 100%; gap: 10%; justify-content: center;">
                  <div class="letras-adivinadas">
                    <span v-for="letra in palabraActual">{{ letrasAdivinadas.includes(letra) ? letra : '_' }}</span>
                  </div>
                </div>
                <div class="letras">
                  <button v-for="letra in alfabeto" :key="letra" @click="adivinarLetra(letra)"
                    :disabled="letrasAdivinadas.includes(letra) || letrasIncorrectas.includes(letra)">
                    {{ letra }}
                  </button>
                </div>
              </div>
            </div>
          </div>
          <div style="display: flex;"
            v-if="dificultadSeleccionada && temaSeleccionado === 'Marcas' && dificultadSeleccionada === 'Dificil'">
            <div class="vif">
              <div class="vif">
                <img :src="imagenOportunidad">
                <div v-if="palabraAdivinada">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div v-if="palabraIncorrecta">
                  <button @click="seleccionarOtroTema" class="botonImp">Elegir otro tema</button>
                  <button @click="seleccionarOtraDificultad" class="botonImp">Elegir otra dificultad</button>
                </div>
                <div style="display: flex; flex-direction: row; width: 100%; gap: 10%; justify-content: center;">
                  <div class="letras-adivinadas">
                    <span v-for="letra in palabraActual">{{ letrasAdivinadas.includes(letra) ? letra : '_' }}</span>
                  </div>
                </div>
                <div class="letras">
                  <button v-for="letra in alfabeto" :key="letra" @click="adivinarLetra(letra)"
                    :disabled="letrasAdivinadas.includes(letra) || letrasIncorrectas.includes(letra)">
                    {{ letra }}
                  </button>
                </div>
              </div>
            </div>
          </div>
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
import img from '/src/1.jpg'
import img2 from '/src/2.jpg'
import img3 from '/src/3.jpg'
import img4 from '/src/4.jpg'
import img5 from '/src/5.jpg'
import img6 from '/src/6.jpg'
import img7 from '/src/7.jpg'
import img8 from '/src/8.jpg'
import img9 from '/src/9.jpg'
import img10 from '/src/10.jpg'
import img11 from '/src/11.jpg'


const juegoGanado = ref(false);
const juegoPerdido = ref(false);
const imagenesOportunidad = [img2, img3, img4, img5, img6, img7, img8, img9];
const oportunidadesIncorrectas = ref(0);
const imagenOportunidad = ref(img);
const imagenesOportunidadMedio = [img5, img6, img7, img8, img9,];
const temas = ref(false)
const temaSeleccionado = ref(null);
const dificultadSeleccionada = ref(null);
const temasInfo = {
  Animales: {
    Facil: {
      palabras: ['GATO', 'PERRO', 'CONEJO', 'RATON'],
      oportunidadesIncorrectas: -1,
      imagenOportunidad: img,
    },
    Medio: {
      palabras: ['ORANGUTAN', 'COCODRILO', 'RINOCERONTE', 'ARMADILLO'],
      oportunidadesIncorrectas: 2,
      imagenOportunidad: img,
    },
    Dificil: {
      palabras: ['ORNITORRINCO', 'TARANTULA', 'CANGURO', 'LEOPARDO'],
      oportunidadesIncorrectas: 5,
      imagenOportunidad: img,
    },
  }, Frutas: {
    Facil: {
      palabras: ['MANZANA', 'BANANA', 'UVA', 'PERA'],
      oportunidadesIncorrectas: -1,
      imagenOportunidad: img,
    },
    Medio: {
      palabras: ['NARANJA', 'SANDÍA', 'KIWI', 'CEREZA'],
      oportunidadesIncorrectas: 2,
      imagenOportunidad: img,
    },
    Dificil: {
      palabras: ['GUAYABA', 'MANGO', 'FRAMBUESA', 'PIÑA'],
      oportunidadesIncorrectas: 5,
      imagenOportunidad: img,
    },
  }, Ciudades: {
    Facil: {
      palabras: ['PARIS', 'LONDRES', 'ROMA', 'MADRID'],
      oportunidadesIncorrectas: -1,
      imagenOportunidad: img,
    },
    Medio: {
      palabras: ['NUEVA YORK', 'TOKIO', 'BERLIN', 'MOSCU'],
      oportunidadesIncorrectas: 2,
      imagenOportunidad: img,
    },
    Dificil: {
      palabras: ['SINGAPUR', 'DUBAI', 'SYDNEY', 'RIO DE JANEIRO'],
      oportunidadesIncorrectas: 5,
      imagenOportunidad: img,
    },
  },
  Colores: {
    Facil: {
      palabras: ['ROJO', 'VERDE', 'AZUL', 'AMARILLO'],
      oportunidadesIncorrectas: -1,
      imagenOportunidad: img,
    },
    Medio: {
      palabras: ['NARANJA', 'VIOLETA', 'CELESTE', 'GRIS'],
      oportunidadesIncorrectas: 2,
      imagenOportunidad: img,
    },
    Dificil: {
      palabras: ['MAGENTA', 'TURQUESA', 'ESMERALDA', 'CARMESI'],
      oportunidadesIncorrectas: 5,
      imagenOportunidad: img,
    },
  },
  Marcas: {
    Facil: {
      palabras: ['NIKE', 'ADIDAS', 'PUMA', 'REEBOK'],
      oportunidadesIncorrectas: -1,
      imagenOportunidad: img,
    },
    Medio: {
      palabras: ['APPLE', 'SAMSUNG', 'SONY', 'MICROSOFT'],
      oportunidadesIncorrectas: 2,
      imagenOportunidad: img,
    },
    Dificil: {
      palabras: ['FERRARI', 'LAMBORGHINI', 'BUGATTI', 'MASERATI'],
      oportunidadesIncorrectas: 5,
      imagenOportunidad: img,
    },
  },
};

const palabraSeleccionada = ref(null);
const letrasAdivinadas = ref([]);
const letrasIncorrectas = ref([]);
const palabraActual = ref('');
const palabraAdivinada = ref(false);
const palabraIncorrecta = ref(false);


const alfabeto = ref(['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z']);


function iniTemas() {
  temas.value = true;
  temaSeleccionado.value = null;
}


function seleccionarTema(tema) {
  temaSeleccionado.value = tema;
}

function seleccionarDificultad(dificultad) {
  dificultadSeleccionada.value = dificultad;

  if (temaSeleccionado.value && dificultadSeleccionada.value) {
    const temaInfo = temasInfo[temaSeleccionado.value];
    const dificultadInfo = temaInfo[dificultadSeleccionada.value];

    palabraSeleccionada.value = dificultadInfo.palabras[Math.floor(Math.random() * dificultadInfo.palabras.length)];
    oportunidadesIncorrectas.value = dificultadInfo.oportunidadesIncorrectas;
    imagenOportunidad.value = dificultadInfo.imagenOportunidad;

    palabraActual.value = palabraSeleccionada.value;
  }
}


function adivinarLetra(letra) {
  if (!juegoGanado.value && !juegoPerdido.value) {
    if (palabraSeleccionada.value && !letrasAdivinadas.value.includes(letra) && !letrasIncorrectas.value.includes(letra)) {
      if (palabraSeleccionada.value.includes(letra)) {
        letrasAdivinadas.value.push(letra);
        palabraActual.value = palabraSeleccionada.value
          .split('')
          .map(char => (letrasAdivinadas.value.includes(char) ? char : '_'))
          .join('');
        if (palabraActual.value === palabraSeleccionada.value) {
          juegoGanado.value = true;
          palabraAdivinada.value = true;
          imagenOportunidad.value = img10;
          console.log('¡Ganaste!');
        }
      } else {
        letrasIncorrectas.value.push(letra);
        oportunidadesIncorrectas.value++;

        if (oportunidadesIncorrectas.value < imagenesOportunidad.length) {
          imagenOportunidad.value = imagenesOportunidad[oportunidadesIncorrectas.value];
        } else {
          imagenOportunidad.value = img11;
          juegoPerdido.value = true;
          palabraIncorrecta.value = true;
          console.log('¡Perdiste!');
        }
      }
    }
  }
}

function reiniciarJuego() {
  juegoGanado.value = false;
  juegoPerdido.value = false;
  oportunidadesIncorrectas.value = 0;
  imagenOportunidad.value = img;
  temaSeleccionado.value = null;
  dificultadSeleccionada.value = null;
  palabraSeleccionada.value = null;
  letrasAdivinadas.value = [];
  letrasIncorrectas.value = [];
  palabraActual.value = '';
  palabraAdivinada.value = false;
  palabraIncorrecta.value = false;
}

function reiniciarJuegodos() {
  juegoGanado.value = false;
  juegoPerdido.value = false;
  oportunidadesIncorrectas.value = 0;
  imagenOportunidad.value = img;
  dificultadSeleccionada.value = null;
  palabraSeleccionada.value = null;
  letrasAdivinadas.value = [];
  letrasIncorrectas.value = [];
  palabraActual.value = '';
  palabraAdivinada.value = false;
  palabraIncorrecta.value = false;
}

function seleccionarOtroTema() {
  temaSeleccionado.value = null;
  dificultadSeleccionada.value = null;
  reiniciarJuego();
}

function seleccionarOtraDificultad() {
  dificultadSeleccionada.value = null;
  reiniciarJuegodos();
}
</script>

<style>
img {
  height: 400px;
}

section {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  min-height: 100vh;
  background: linear-gradient(rgb(250, 189, 74), rgb(34, 34, 150));
}

#inicio {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 25px;
}

#jugar {
  width: 170px;
  height: 40px;
  font-size: 20px;
  border: 0;
  border-radius: 5px;
  background-color: rgb(208, 208, 255);
}

#jugar:hover {
  background: rgb(253, 239, 214);
  cursor: pointer;
}

.tema {
  width: 170px;
  height: 40px;
  font-size: 20px;
  border: 0;
  border-radius: 5px;
  background-color: rgb(208, 208, 255);
}

.tema:hover {
  background: rgb(253, 239, 214);
  cursor: pointer;

}

.vif {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 55px;
}

.letras {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  width: 1000px;
  gap: 5px;
}

.letras button {
  width: 100px;
  height: 30px;
}

.letras-adivinadas {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 50%;
  gap: 10px;
}

.letras-adivinadas .letra-adivinada {
  text-align: center;
  width: 30px;
  font-size: 24px;
  color: rgb(253, 239, 214);
}

.botonImp{
  background: linear-gradient(rgb(255, 206, 115), rgb(114, 114, 255));
  /* background-color: rgb(126, 126, 222); */
  border-radius: 50px;
  border: 0;
  height: 40px;
  width: 150px;
  font-family: 'Franklin Gothic Medium';
  margin-left: 15px;
}

.botonImp:hover{
  background-color: rgb(239, 203, 137);
  cursor: pointer;
  height: 45px;
  width: 155px;
}
</style>
