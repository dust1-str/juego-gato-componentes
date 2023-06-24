<script setup>
import { ref } from 'vue';

let usuarios = ref(true);
let usuario1 = ref('');
let usuario2 = ref('');

const quitar = () => {
  usuarios.value = false;
}
</script>

<template>
    <div v-show="usuarios" class="usuarios">
      <div class="user1">
        <h1>Jugador uno</h1>
        <input v-model="usuario1" type="text" placeholder="Nombre del jugador uno">
      </div>
      <div class="user2">
        <h1>Jugador dos</h1>
        <input v-model="usuario2" type="text" placeholder="Nombre del jugador dos">
        <button @click="$emit('jugar', {
            user1: usuario1,
            user2: usuario2
        }), quitar()">JUGAR!</button>
      </div>
    </div>
</template>

<style scoped>
    .usuarios {
        display: flex;
        justify-content: space-around;
    }

    input {
        height: 30px;
        margin-right: 10px;
    }
</style>