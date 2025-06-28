<script setup>
    import { ref } from 'vue'
    import Score from './Score.vue';

    let scoreTotal = ref(0)
</script>

<template>
    <header class="header">
        <div class="name">ЗАПОМНИ СЛОВО</div>
        <Score :score="scoreTotal"/>
    </header>
</template>

<style scoped>
.header {
    padding: 50px 62px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
</style>