<script setup lang="ts">
defineProps({
  buttonAction: {
    type: Function,
    required: true,
  },
});
</script>

<template>
  <button class="base__button" v-on:click.prevent="() => buttonAction()">
    <slot></slot>
  </button>
</template>

<style scoped lang="scss">
.base__button {
  line-height: 16px;
  color: #fff;
  text-align: center;
  font-family: Bahnschrift;
  font-size: 16px;
  font-style: normal;
  font-weight: 600;
  line-height: normal;
  border-radius: 12px;
  border: 1px solid #4456fe;
  background-color: #4456fe;
  height: 100%;
  width: 100%;
  max-width: 500px;
  user-select: none;
  cursor: pointer;
}

@media screen and (max-width: 639px) {
  .base__button {
    max-width: 320px;
  }
}
</style>
