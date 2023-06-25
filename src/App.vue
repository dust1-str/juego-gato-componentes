<template>
  <Usuarios @jugar="user"/>
  <div class="historial">
    <Tablero @ganador="mostrarGanador"/>
    <Resultados :ganadores="{
      g1: ganadores[0]
    }"/>
  </div>
  <Turnos :users="{
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

let usuario1 = ref('');
let usuario2 = ref('');

let ganadores = ref({});

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
  if (ganador === 'X')
    ganadores.value[0] = usuario1.value;
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