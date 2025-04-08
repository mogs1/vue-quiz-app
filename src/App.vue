<template>
  <div class="flex justify-center items-center ">
    <component
      :is="currentComponent"
      :score="score"
      :onNext="nextView"
      :restartGame="restartGame"
      :updateScore="updateScore"
    />
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import TapRevealView from './views/TapRevealView.vue';
import GameView from './views/GameView.vue';
import ResultView from './views/ResultView.vue';

const view = ref('tap');
const score = ref(0);

const nextView = () => {
  if (view.value === 'tap') view.value = 'game';
  else if (view.value === 'game') view.value = 'result';
};

const restartGame = () => {
  score.value = 0;
  view.value = 'tap';
};

const updateScore = () => score.value++;

const currentComponent = computed(() => {
  if (view.value === 'tap') return TapRevealView;
  if (view.value === 'game') return GameView;
  if (view.value === 'result') return ResultView;
});
</script>
