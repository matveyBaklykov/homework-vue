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
        padding: 16px 10px;
        border-radius: 100px;
        border: none;
        background: var(--color-dark-blue);
        width: 335px;
        cursor: pointer;
    }

    .button:hover {
        background: var(--color-btn-darker);
        
    }
</style>