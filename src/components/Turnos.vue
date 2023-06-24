<script setup>
defineProps ({
  users : {
    type: Object
  }
})

</script>

<template>
    <h1>Turno de:</h1>
    <div class="jugadores">
      <div class="user">
        {{ users.user1 }}
      </div>
      <div class="user">
        {{ users.user2 }}
      </div>
    </div> 
</template>

<style scoped>
.jugadores {
    display: flex;
    justify-content: space-around;
    background-color: aquamarine;
    height: 100px;
    align-items: center;
}

.user {
  display: flex;
  align-items: center;
  background-color: azure;
  height: 40%;
  width: min-content;
  padding: 0 0.5em;
  border-radius: 5px;
}
</style>