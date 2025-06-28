<script setup>
import IconHeart from '../icons/IconHeart.vue';

    const { score } = defineProps({
        score: Number,
    })
</script>

<template>
    <div class="score">
        <p class="score-text">{{ score }}</p>
        <IconHeart />
    </div>
</template>

<style scoped>
    .score {
        width: 110px;
        border-radius: 36px;
        /* padding: 12px 24px; */
        border: none;
        background: #cce8ff;
        color: var(--color-dark-blue);
        box-shadow: 0 0 4px 0 rgba(0, 0, 0, 0.15);
        height: 48px;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 10px;
    }
    .score-text {
        font-weight: 700;
    }
</style>