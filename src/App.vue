<script setup>
  import { ref } from 'vue'
  import Button from './components/Button.vue';
  import Card from './components/Card.vue';
  import Header from './components/Header.vue';

  const gameStarted = ref(false)

  let totalScore = ref(0)

  let cards = ref([
    {
      word: 'unadmitted',
      translation: 'непризнанный',
      state: "closed", // closed or open
      status: "pending" // sucess, fail or pending
    }, 
    {
      word: 'armour-piercer',
      translation: 'бронебойщик',
      state: "closed", 
      status: "pending" 
    },
    {
      word: 'stamen',
      translation: 'тычинка',
      state: "closed", 
      status: "pending" 
    },
    {
      word: 'vino',
      translation: 'вино',
      state: "closed", 
      status: "pending" 
    },
    {
      word: 'pollination',
      translation: 'опыление',
      state: "closed", 
      status: "pending" 
    },
    
  ])

  const startGame = () => {
    gameStarted.value = true
  }
</script>

<template>
  <Header :totalScore="totalScore"></Header>
  <main class="main">
    <div class="cards">
      <Card v-if="gameStarted" :card="card" v-for="( card, index )  in cards" :key="index" :index="index"/>
    </div>
    
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
    padding: 49px 66px;
    flex-wrap: wrap;
  }

  .cards {
    display: flex;
    gap: 107px;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
  }
</style>
