<script setup>
  import { ref } from 'vue'
  import Button from './components/Button.vue';
  import Card from './components/Card.vue';
  import Header from './components/Header.vue';

  const gameStarted = ref(false)

  let totalScore = ref(0)

  let cardInfo = ref({
  word: 'unadmitted',
  translation: 'непризнанный',
  state: "closed", // closed or open
  status: "pending" // sucess, fail or pending
})

  const startGame = () => {
    gameStarted.value = true
  }
</script>

<template>
  <Header :totalScore="totalScore"></Header>
  <main class="main">
    <Card v-if="gameStarted" :cardInfo="cardInfo"/>
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
