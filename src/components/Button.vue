<script setup>

</script>

<template>
    <button class="button">
        <slot></slot>
    </button>
  
</template>

<style scoped>
    .button {
        color: var(--color-primary);
        font-weight: 400;
        font-size: 24px;
        padding: 10px 16px;
        border-radius: 16px;
        border: none;
        background: var(--color-btn);
        min-width: 315px;
        cursor: pointer;
    }

    .button:hover {
        background: var(--color-btn-darker);
        
    }
</style>