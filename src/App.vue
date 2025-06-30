<script setup>
  import { computed, ref } from 'vue'
  import Button from './components/Button.vue';
  import Card from './components/Card.vue';
  import Header from './components/Header.vue';

  const gameStarted = ref(false)
  const API_CARDS = 'http://localhost:8080/api/random-words'

  let totalScore = ref(0)

  let cards = ref([])

  let cardsModifyed = ref([])

  const startGame = async () => {
    const res = await fetch(API_CARDS)
    cards.value = await res.json()

    cardsModifyed.value = cards.value.map((card) => ({
      word: card.word,
      translation: card.translation,
      state: "closed",
      status: "pending"
    }))


    gameStarted.value = true
  }

  
</script>

<template>
  <Header :totalScore="totalScore"></Header>
  <main class="main">
    <div class="cards">
      <Card v-if="gameStarted" :card="card" v-for="(card, index) in cardsModifyed" :key="card.word" :index="index"/>
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
    align-items: center;
    flex-wrap: wrap;
  }
</style>
