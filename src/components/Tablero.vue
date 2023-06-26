<script setup>
import { ref } from 'vue';

let posiciones = ref(['-','-','-','-','-','-','-','-','-',]);

let presionar = ref('');
let turno = 'X';
let juego = true;
let ganador = ref('');
let casillas = 0;

const emit = defineEmits(['ganador']);

const enviarGanador = value => {
  emit('ganador', value);
}


const asignarLetra = (i) => {
  if (turno === 'X' && juego && casillas != 9){
    posiciones.value[i] = 'X';
    turno = 'O';
    presionar.value = 'background-color: green'
  } else if (turno === 'O' && juego && casillas != 9){
    posiciones.value[i] = 'O';
    turno = 'X';
  }
  casillas++;
  verificarCeldas(posiciones.value[0],posiciones.value[1],posiciones.value[2]);
  verificarCeldas(posiciones.value[3],posiciones.value[4],posiciones.value[5]);
  verificarCeldas(posiciones.value[6],posiciones.value[7],posiciones.value[8]);
  verificarCeldas(posiciones.value[0],posiciones.value[4],posiciones.value[8]);
  verificarCeldas(posiciones.value[2],posiciones.value[4],posiciones.value[6]);
  verificarCeldas(posiciones.value[0],posiciones.value[3],posiciones.value[6]);
  verificarCeldas(posiciones.value[1],posiciones.value[4],posiciones.value[7]);
  verificarCeldas(posiciones.value[2],posiciones.value[5],posiciones.value[8]);
};

const verificarCeldas = (c1, c2, c3) => {
  if (c1 === c2 && c2 === c3 && c1 != '-' && juego){
    ganador.value = c1;
    mostrarGanador();
  }
}

const mostrarGanador = () => {
  if (ganador.value === 'X')
    console.log('Usuario1 ha ganado')
  else if (ganador.value === 'O')
    console.log('Gano el otro')
  enviarGanador(ganador.value);  
  juego = false;    
}

const reiniciarJuego = () => {
  if (!juego) {
    for (let i = 0; i <= 8; i++){
    posiciones.value[i] = '-';
    };
  }
  juego = true;
  turno = 'X';
}
</script>

<template>
    <div class="tablero">
      <div class="boton">
        <button @click.prevent="asignarLetra(0)">{{ posiciones[0] }}</button>
      </div>
      <div class="boton">
        <button @click.prevent="asignarLetra(1)">{{ posiciones[1] }}</button>
      </div>
      <div class="boton">
        <button @click.prevent="asignarLetra(2)">{{ posiciones[2] }}</button>
      </div>
      <div class="boton">
        <button @click.prevent="asignarLetra(3)">{{ posiciones[3] }}</button>
      </div>
      <div class="boton">
        <button @click.prevent="asignarLetra(4)">{{ posiciones[4] }}</button>
      </div>
      <div class="boton">
        <button @click.prevent="asignarLetra(5)">{{ posiciones[5] }}</button>
      </div>
      <div class="boton">
        <button @click.prevent="asignarLetra(6)">{{ posiciones[6] }}</button>
      </div>
      <div class="boton">
        <button @click.prevent="asignarLetra(7)">{{ posiciones[7] }}</button>
      </div>
      <div class="boton">
        <button @click.prevent="asignarLetra(8)">{{ posiciones[8] }}</button>
      </div>
    </div>
    <div class="reiniciar">
      <button @click="reiniciarJuego">Reiniciar</button>
    </div>
    
</template>

<style scoped>

.tablero {
    background-color: blue;
    display: grid;
    height: 15em;
    width: 50%;
    grid-template-columns: auto auto auto;
    grid-template-rows: auto auto auto;
    margin-top: 2em;
}

.boton {
  border: 2px solid black;
  display: flex;
  justify-content: center;
  align-items: center;
}

.boton button {
  height: 50px;
  width: 50px;
}

.reiniciar {
  background-color: bisque;
  display: flex;
  height: min-content;
  width: min-content;
  justify-content: center;
  align-items: center;
  margin-top: 8.4em;
  margin-left: 2em;
  margin-right: 2em;
}

.reiniciar button {
  height: 40px;
  width: min-content;
}
</style>