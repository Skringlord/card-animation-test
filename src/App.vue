<script setup lang="ts">
import GameCard from "../src/components/gameCard/GameCard.vue";
import MovableCard from "../src/components/movableCard/movableCard.vue";
import BaseButton from "../src/components/ui/baseButton/BaseButton.vue";
import { ref, reactive } from "vue";
import type { Ref } from "vue";

const gameContainer: Ref<Element | undefined> = ref();
const movableCards = reactive([1]);

let cardCounter: number = 0;
let cardTransitionFinished: boolean = true;

function handleAnimation() {
  if (cardTransitionFinished && gameContainer?.value) {
    cardTransitionFinished = false;
    const lastPlayCardIndex = gameContainer.value.children.length;
    const lastPlayCard = gameContainer.value.children[lastPlayCardIndex - 1];
    cardCounter++;
    lastPlayCard.classList.toggle("roll__move__card");
    setTimeout(() => {
      cardTransitionFinished = true;
      movableCards.push(cardCounter);
    }, 1850);
  }
}
</script>

<template>
  <div class="main__game__container" ref="gameContainer">
    <GameCard />
    <GameCard />
    <GameCard />
    <MovableCard v-for="card in movableCards" :key="card" :zIndex="card" />
  </div>
  <div class="game__controls__container">
    <BaseButton :button-action="handleAnimation">Play</BaseButton>
  </div>
</template>

<style lang="scss" scoped>
.main__game__container {
  display: flex;
  flex-direction: row;
  max-width: 595px;
  margin-bottom: 50px;
  column-gap: 20px;
  justify-content: center;
}
.game__controls__container {
  height: 73px;
}

@media screen and (max-width: 639px) {
  .main__game__container {
    column-gap: 10px;
  }
}
</style>
