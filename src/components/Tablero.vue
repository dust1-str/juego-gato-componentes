<script setup>
import { ref } from 'vue';

let posiciones = ref(['-','-','-','-','-','-','-','-','-',])

const asignarLetra = (i) => {
  if (turno === 'X' && juego && casillas != 9){
    posiciones.value[i] = 'X';
    turno = 'O';
  } else if (turno === 'O' && juego && casillas != 9){
    posiciones.value[i] = 'O';
    turno = 'X';
  }
  casillas++;
  mostrarTurno();
  verificarCeldas(posiciones.value[0],posiciones.value[1],posiciones.value[2]);
  verificarCeldas(posiciones.value[3],posiciones.value[4],posiciones.value[5]);
  verificarCeldas(posiciones.value[6],posiciones.value[7],posiciones.value[8]);
  verificarCeldas(posiciones.value[0],posiciones.value[4],posiciones.value[8]);
  verificarCeldas(posiciones.value[2],posiciones.value[4],posiciones.value[6]);
  verificarCeldas(posiciones.value[0],posiciones.value[3],posiciones.value[6]);
  verificarCeldas(posiciones.value[1],posiciones.value[4],posiciones.value[7]);
  verificarCeldas(posiciones.value[2],posiciones.value[5],posiciones.value[8]);
};
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
</template>

<style scoped>

.tablero {
    background-color: red;
    display: grid;
    width: 50%;
    grid-template-columns: auto auto auto;
    grid-template-rows: auto auto auto;
    align-items: center;
    justify-content: center;
    margin-top: 2em;
}
</style>