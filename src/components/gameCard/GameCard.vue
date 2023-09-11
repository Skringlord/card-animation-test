<script setup lang="ts">
import cardBacksideBackground from "../../assets/cardBacksideBackground.svg";
</script>

<template>
  <div class="card__main__container"><img :src="cardBacksideBackground" /></div>
</template>

<style scoped lang="scss">
.card__main__container {
  height: 260px;
  width: 185px;
  background-color: #1660b6;
  border-radius: 20px;
  border: 9px solid #555660;
  box-sizing: border-box;
  user-select: none;
  overflow: hidden;
}

@media screen and (max-width: 639px) {
  .card__main__container {
    height: 138px;
    width: 92.5px;
    border-radius: 10px;
    border: 4.5px solid #555660;
  }
}
</style>
