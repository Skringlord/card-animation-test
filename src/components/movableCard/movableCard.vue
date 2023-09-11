<script setup lang="ts">
import cardSuit from "../../assets/icons/cardType.svg";
import GameCard from "../gameCard/GameCard.vue";

defineProps({
  zIndex: {
    type: Number,
    required: true,
  },
});
</script>

<template>
  <div class="movable__card__main__container">
    <div class="movable__card__inner__container">
      <GameCard />
      <div class="card__front__container">
        <div class="card__value__container">
          <p class="card__front__type">A</p>
          <img :src="cardSuit" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.movable__card__main__container {
  height: 260px;
  width: 185px;
  background-color: transparent;
  margin-left: auto;
  margin-right: auto;
  box-sizing: border-box;
  position: absolute;
  z-index: v-bind(zIndex);
}
.movable__card__inner__container {
  perspective: 1500px;
  width: 100%;
  height: 100%;
  transition: all 0.85s;
  transform-style: preserve-3d;
  box-sizing: border-box;
}
.card__front__container {
  background-color: white;
  width: 100%;
  height: 100%;
  position: inherit;
  transform: rotateY(-180deg);
  padding-top: 5px;
  padding-left: 10px;
}
.card__main__container,
.card__front__container {
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
  position: absolute;
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  border-radius: 20px;
}
.card__value__container {
  display: flex;
  width: max-content;
  flex-direction: column;
  align-items: start;
  row-gap: 4px;
  & > p {
    width: 100%;
    color: #000;
    text-align: center;
    font-family: Bahnschrift;
    font-size: 24px;
    font-style: normal;
    font-weight: 600;
    line-height: 24px;
    margin: 0;
  }
}
.roll__move__card {
  & > .movable__card__inner__container {
    animation: cardRollAnimation 0.5s forwards;
  }
  animation: cardPushUpTopAnimation 1s ease-in 0.5s forwards,
    cardPushDownTopAnimation 0.5s ease-in 1s forwards;
}

@media screen and (max-width: 639px) {
  .movable__card__main__container {
    height: 138px;
    width: 92.5px;
  }

  .movable__card__main__container,
  .card__front__container,
  .card__main__container {
    border-radius: 10px;
  }

  .roll__move__card {
    animation: cardPushUpTopAnimation 1s ease-in 0.5s forwards,
      cardPushDownTopMobileAnimation 0.5s ease-in 1s forwards;
  }
}
</style>
