<script setup>
import { ref } from 'vue';

// Position of the "Yes" button
const posX = ref(0);
const posY = ref(0);

// Move button to a random position
const moveAway = () => {
  const maxX = window.innerWidth - 100; // adjust for button width
  const maxY = window.innerHeight - 50; // adjust for button height
  posX.value = Math.floor(Math.random() * maxX);
  posY.value = Math.floor(Math.random() * maxY);
};
</script>

<template>
  <div class="relative h-screen w-screen bg-pink-600 overflow-hidden">
    <button
      class="absolute px-4 py-2 bg-white text-black rounded"
      :style="{ left: posX + 'px', top: posY + 'px' }"
      @mouseenter="moveAway"
    >
      Yes
    </button>

    <button
      class="absolute bottom-10 left-10 px-4 py-2 bg-white text-black rounded"
    >
      No
    </button>
  </div>
</template>
