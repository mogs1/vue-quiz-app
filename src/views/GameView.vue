<template>
  <div class="p-6 text-center">
    <!-- ProgressBar only in this view -->
    <ProgressBar :step="currentCardIndex + 1" :total="cards.length" />

    <div v-if="currentCardIndex < cards.length" class="mt-6">
      <div class="relative">
        <div
          class="bg-white shadow-lg h-64 flex justify-center item-center p-8 rounded-2xl transition-all duration-500"
          :style="{ background: cards[currentCardIndex].color }"
        >
          <h2 class="text-white text-center text-xl font-bold">
            {{ cards[currentCardIndex].text }}
          </h2>
        </div>
      </div>

      <!-- Arrow Controls -->
      <div class="flex justify-between gap-4 mt-6">
        <button
          @click="handleSwipe('physical')"
          class="bg-blue-500 text-white px-4 py-2 rounded-xl"
        >
          ← Physical Change
        </button>
        <button
          @click="handleSwipe('chemical')"
          class="bg-purple-500 text-white px-4 py-2 rounded-xl"
        >
          Chemical Change →
        </button>
      </div>
    </div>

    <div v-else class="mt-10">
      <h2 class="text-2xl font-bold">Great Job!</h2>
      <p class="mt-2 text-lg text-gray-700">You scored {{ score }} out of {{ cards.length }}</p>
      <button @click="onNext" class="mt-4 bg-green-600 text-white px-4 py-2 rounded-xl">
        want to play again?
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import ProgressBar from './ProgressBar.vue';
import cards from '@/components/Card';

const props = defineProps(['onNext']);
const score = ref(0);
const currentCardIndex = ref(0);

const handleSwipe = (direction) => {
  const currentCard = cards[currentCardIndex.value];
  if (currentCard.answer === direction) {
    score.value++;
  }
  currentCardIndex.value++;
};
</script>
