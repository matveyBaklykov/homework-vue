<script setup></script>

<template>
    <div class="card">
      <div class="card-side card-front">
        <div class="inner-border">
          <div class="word">unadmitted</div>
          <div class="number">01</div>
          <div class="flip">ПЕРЕВЕРНУТЬ</div>
        </div>
      </div>
    </div>
</template>

<style scoped>

    .card {
      width: 250px;
      height: 376px;
      position: relative;
      cursor: pointer;
    }

    .card-side {
      position: absolute;
      width: 100%;
      height: 100%;
      background: var(--color-primary);
      border-radius: 16px;
      border: none;
      box-shadow: 0 0 16px 0 rgba(0, 0, 0, 0.1);
    }

    .card-front {
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .inner-border {
      position: relative;
      width: 212px;
      height: 320px;
      border: 1px solid #cce8ff;
      border-radius: 12px;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .word {
        font-weight: 400;
        font-size: 18px;
    }

    .number {
      position: absolute;
      top: -8px;
      left: 10px;
      font-weight: 400;
        font-size: 18px;
      background: white;
      padding: 0 4px;
    }

    .flip {
      position: absolute;
      bottom: -8px;
      left: 50%;
      transform: translateX(-50%);
      font-size: 12px;
      background: white;
      padding: 0 6px;
      font-size: 12px;
      font-weight: 500;
    }
</style>