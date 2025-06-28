<script setup>
    import Score from './Score.vue';

    const score = 100
</script>

<template>
    <header class="header">
        <div class="name">ЗАПОМНИ СЛОВО</div>
        <Score :score="score"/>
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