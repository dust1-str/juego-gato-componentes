<script setup>
let winner = false;

defineProps ({
    ganadores: {
        type: Object
    },
    jugadores: {
        type: Object
    }
});
</script>

<template>
    <div class="puntos">
        <div class="tabla">
            <h1>Tabla de puntuacion</h1>
        </div>
        <div class="points">
            <div class="puntos-u1">
                <div class="jugador">
                    <h1>{{ jugadores.user1 }}</h1>
                </div>
            <div class="score">
                <li v-show="ganadores.g1">1</li>
                <li v-show="ganadores.g3">2</li>
                <li v-show="ganadores.g5">3</li>
                <li v-show="ganadores.g7">4</li>
                <li v-show="ganadores.g9">5</li>
            </div>
            </div>
            <div class="puntos-u2">
                <div class="jugador-dos">
                    <h1>{{ jugadores.user2 }}</h1>
                </div>
            <div class="score">
                <li v-show="ganadores.g2">1</li>
                <li v-show="ganadores.g4">2</li>
                <li v-show="ganadores.g6">3</li>
                <li v-show="ganadores.g8">4</li>
                <li v-show="ganadores.g10">5</li>
            </div>
        </div>
        </div>
    </div>
</template>

<style scoped>
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }
    .puntos {
        display: flex;
        flex-direction: column;
        background-color: bisque;
        margin-top: 2em;
        height: 15em;
        width: 40%;
        justify-content: space-around;
    }
    .points {
        display: flex;
        justify-content: space-around;
    }

    .tabla {
        display: flex;
        justify-content: center;
        background-color: aqua;
    }

    .score {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-top: 0.5em;
    }

    li {
        list-style: none;
    }
</style>