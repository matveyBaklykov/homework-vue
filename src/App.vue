<script setup>
  import { ref } from 'vue'
  import Button from './components/Button.vue';
  import Card from './components/Card.vue';
  import Header from './components/Header.vue';

  const gameStarted = ref(false)

  const startGame = () => {
    gameStarted.value = true
  }
</script>

<template>
  <Header ></Header>
  <main class="main">
    <Card v-if="gameStarted"/>
    <Button v-show="!gameStarted" @click="startGame">
    Начать игру
    </Button>
  </main>
  
  
</template>

<style scoped>
  .main {
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
