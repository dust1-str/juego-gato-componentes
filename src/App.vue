<template>
  <Usuarios @jugar="user"/>
  <div class="historial">
    <Tablero @ganador="mostrarGanador"/>
    <Resultados :jugadores="{
    user1: usuario1,
    user2: usuario2
  }" :ganadores="{
      g1: ganadores[0],
      g2: ganadores[1],
      g3: ganadores[2],
      g4: ganadores[3],
      g5: ganadores[4],
      g6: ganadores[5],
      g7: ganadores[6],
      g8: ganadores[7],
      g9: ganadores[8],
      g10: ganadores[9]
    }"/>
  </div>
  <Turnos :users="{
    user1: usuario1,
    user2: usuario2
  }"/>
  <Mensaje :ganador="winner" :jugadores="{
    user1: usuario1,
    user2: usuario2
  }"/>
</template>

<script setup>
import { ref } from 'vue';
import Turnos from './components/Turnos.vue';
import Usuarios from './components/Usuarios.vue';
import Tablero from './components/Tablero.vue';
import Resultados from './components/Resultados.vue';
import Mensaje from './components/Mensaje.vue';

let usuario1 = ref('');
let usuario2 = ref('');
let i = 0;
let j = 1;
let winner = ref(0);

let ganadores = ref(['','','','','','','','','','']);

//Asigna los nombres de los usuarios cuando se presiona 'Jugar'
const user = x =>{
  if (x.user1 != '' && x.user2 != ''){
    usuario1.value = x.user1;
    usuario2.value = x.user2;
  }
  else
    alert('Falta un usuario por asignar');  
}

const mostrarGanador = ganador => {
  if (ganador === 'X'){
    ganadores.value.splice(i,1,usuario1.value);
    i+=2;
    console.log(i);
  }
  else if (ganador === 'O'){
    ganadores.value.splice(j,1,usuario2.value);
    j+=2;
    console.log(j); 
  }    
  signWinner();
}

const signWinner = () => {
  if (i == 10){
    winner.value = 9;
  } else if (j == 11){
    winner.value = 10;
  }
}
</script>

<style scoped>
  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  .historial {
    display: flex;
  }
</style>