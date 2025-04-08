<template>
  <div class="p-6">
    <h2 class="text-center text-xl text-blue-50 font-semibold my-6">Tap to Discover States of Matter!</h2>

    <div class="grid grid-cols-2 gap-6 justify-items-center">
      <div
        v-for="(item, index) in items"
        :key="index"
        class="relative w-40 h-56 perspective"
        @click="flip(index)"
      >
        <div
          class="absolute inset-0 transition-transform duration-500"
          :class="[
            'rounded-xl shadow-lg text-white cursor-pointer transform-style-preserve-3d',
            item.flipped ? 'rotate-y-180' : '',
          ]"
        >
          <!-- Front -->
          <div
            class="absolute inset-0 flex flex-col justify-center items-center backface-hidden rounded-xl"
            :style="{ background: item.color }"
          >
            <component :is="item.icon" class="w-8 h-8 mb-2" />
            <p class="font-semibold text-lg">{{ item.title }}</p>
          </div>

          <!-- Back -->
          <div
            class="absolute inset-0 flex justify-center items-center backface-hidden rotate-y-180 rounded-xl bg-blue-100 text-gray-800 text-center px-2"
          >
            <p>{{ item.description }}</p>
          </div>
        </div>
      </div>
    </div>

    <div class="text-center mt-10">
      <button class="bg-blue-600 text-white px-6 py-2 rounded-full" @click="onNext">Next →</button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { Flame, Droplet, Snowflake, Zap } from 'lucide-vue-next';

const props = defineProps(['onNext']);

const items = ref([
  {
    title: 'Steam',
    description: 'Steam is a gas form of water, it is formed when water is heated.',
    flipped: false,
    color: 'linear-gradient(to right, #06beb6, #48b1bf)',
    icon: Flame,
  },
  {
    title: 'Liquid',
    description: 'A substance that flows freely but is of constant volume, having a consistency like that of water or oil.',
    flipped: false,
    color: 'linear-gradient(to right, #a18cd1, #fbc2eb)',
    icon: Droplet,
  },
  {
    title: 'Ice',
    description: 'Ice is the solid form of water.',
    flipped: false,
    color: 'linear-gradient(to right, #f7971e, #ffd200)',
    icon: Snowflake,
  },
  {
    title: 'Lightning',
    description: 'Lightning is plasma – the fourth state.',
    flipped: false,
    color: 'linear-gradient(to right, #1e3c72, #2a5298)',
    icon: Zap,
  },
]);

const flip = (index) => {
  items.value[index].flipped = !items.value[index].flipped;
};
</script>

<style scoped>
.perspective {
  perspective: 1000px;
}
.transform-style-preserve-3d {
  transform-style: preserve-3d;
}
.backface-hidden {
  backface-visibility: hidden;
}
.rotate-y-180 {
  transform: rotateY(180deg);
}
</style>
