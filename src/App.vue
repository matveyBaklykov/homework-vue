<script setup>
  import { computed, ref } from 'vue'
  import Button from './components/Button.vue';
  import Card from './components/Card.vue';
  import Header from './components/Header.vue';

  const gameStarted = ref(false)
  const API_CARDS = 'http://localhost:8080/api/random-words'

  let totalScore = ref(0)

  let cards = ref([])

  const error = ref(null)

  let cardsModifyed = ref([])

  const startGame = async () => {
    try {
      const res = await fetch(API_CARDS)

      if (!res.ok) {
        throw new Error(`Ошибка загрузки: ${res.status} ${res.statusText}`)
      }
      
      cards.value = await res.json()

      cardsModifyed.value = cards.value.map((card) => ({
      word: card.word,
      translation: card.translation,
      state: "closed",
      status: "pending"
    }))

    totalScore.value = 0
    gameStarted.value = true

    } catch (err) {
       console.error('Ошибка при загрузке карточек:', err)
      error.value = 'Не удалось загрузить карточки. Попробуйте позже.'
    }
    
    
  }

  const flipCard = (index) => {
    if (cardsModifyed.value[index].state === 'closed') {
    cardsModifyed.value[index].state = 'open'
    }
  }

  const handleAnswer = ({ index, status }) => {
  if (cardsModifyed.value[index].status !== 'pending') return 

  cardsModifyed.value[index].status = status

  if (status === 'success') {
    totalScore.value += 10
  } else if (status === 'fail') {
    totalScore.value -= 4
  }
}

  
</script>

<template>
  <Header :totalScore="totalScore"></Header>
  <main class="main">
    <div class="cards">
      <Card v-if="gameStarted && cardsModifyed" :card="card" v-for="(card, index) in cardsModifyed" :key="card.word" :index="index" @flip="flipCard(index)" @answer="handleAnswer"/>
    </div>
    <div v-if="error" class="error-message">
      {{ error }}
    </div>
    
    <Button v-show="!gameStarted && !error" @click="startGame">
    Начать игру
    </Button>
    <Button v-if="gameStarted" class="retry" @click="startGame">
      Начать заново
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

  .error-message {
    color: red;
    margin: 16px;
    text-align: center;
  }

  .retry {
    margin-block: 100px;
  }
</style>
