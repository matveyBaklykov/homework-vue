<script setup>
  import Button from './components/Button.vue';
  import Card from './components/Card.vue';
  import Header from './components/Header.vue';
</script>

<template>
  <Header ></Header>
  <main class="main">
    <Card />
    <Button>
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
