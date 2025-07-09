<script setup>
    import { ref } from 'vue'
    import Score from './Score.vue';

    const { totalScore } = defineProps({
        totalScore: Number
    })
</script>

<template>
    <header class="header">
        <div class="name">ЗАПОМНИ СЛОВО</div>
        <Score :score="totalScore"/>
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