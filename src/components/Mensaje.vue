<script setup>
defineProps ({
    ganador: {
        type: Number
    },
    jugadores: {
        type: Object
    }
})
</script>

<template>
    <h1 v-if="ganador == 9">Ha ganado: {{ jugadores.user1 }}</h1>
    <h1 v-if="ganador == 10">Ha ganado: {{ jugadores.user2 }}</h1>
</template>

<style scoped>

h1 {
    text-align: center;
}
</style>