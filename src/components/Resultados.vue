<script setup>

defineProps ({
    ganadores: {
        type: Object
    }
})
</script>

<template>
    <div class="titulo">
        <h1>Ganadores</h1>
        <div>
            <ul>
                <li v-for="i in 5">{{ ganadores.g1 }}</li>
            </ul>
        </div>
    </div>
</template>

<style scoped>
    .titulo {
        display: flex;
        flex-direction: column;
        background-color: bisque;
        margin-top: 2em;
        height: 15em;
        width: 40%;
        align-items: center;
    }

    ul {
        list-style: none;
    }
</style>