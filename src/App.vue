<script setup>
import { ref } from 'vue';
import Turnos from './components/Turnos.vue';
import Usuarios from './components/Usuarios.vue';
import Tablero from './components/Tablero.vue';

let usuario1 = ref('');
let usuario2 = ref('');

//Asigna los nombres de los usuarios cuando se presiona 'Jugar'
const user = x =>{
  if (x.user1 != '' && x.user2 != ''){
    usuario1.value = x.user1;
    usuario2.value = x.user2;
  }
  else
    alert('Falta un usuario por asignar');  
}
</script>

<template>
  <Usuarios @jugar="user"/>
  <Tablero/>
  <Turnos :users="{
    user1: usuario1,
    user2: usuario2
  }"/>
</template>

<style scoped>
  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }
</style>