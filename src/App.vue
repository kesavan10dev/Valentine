<script setup>

  import { ref, onMounted } from 'vue';

  // 1. Declare position refs with safe default values
  const topPos = ref(window.innerHeight / 2.8);
  const leftPos = ref(window.innerWidth / 2);

  // 2. Update positions on resize (use `.value`)
  const updatePosition = () => {
    topPos.value = window.innerHeight / 3;
    leftPos.value = window.innerWidth / 3;
  };

  onMounted(() => {
    window.addEventListener('resize', updatePosition);
  });

  // 3. Move button within screen bounds
  const move = () => {
    const buttonWidth = 150;
    const buttonHeight = 60;
    const buffer = 20;

    const maxLeft = window.innerWidth - buttonWidth - buffer;
    const maxTop = window.innerHeight - buttonHeight - buffer;

    leftPos.value = Math.floor(Math.random() * maxLeft);
    topPos.value = Math.floor(Math.random() * maxTop);
  };

  // 4. Response text
  const ans = ref('');
  const ansf = () => {
    ans.value = "You can’t escape love 😏";
  };
  
</script>



<template>

  <div class=" relative overflow-hidden pt-36 h-screen w-screen bg-pink-700">

    <p class=" top-44 md:top-56 left-16 text-3xl font-extrabold font-mono text-center">Will you accept My proporsal?</p>
    
    <div class=" flex justify-start md:ms-[500px] md:mt-[67px]">
    
        <button class=" p-3 mt-7 mx-12 rounded-xl h-14 sm:w-10 bg-pink-300 border-none font-extrabold text-2xl font-mono text-pink-900" @click="ansf">Yes 😍</button>
      
    </div>

    <button class="absolute p-3 rounded-xl h-14 mx-7 bg-pink-300 font-extrabold text-2xl font-mono text-pink-900 border-none" :style="{ top: topPos + 'px', left: leftPos + 'px' }" @mouseenter="move" @touchstart.prevent="move" @click="move">No 🤷‍♀️</button>

    <p class=" mt-10 text-2xl font-bold font-mono text-center" :key="ans">{{ ans }}</p>

  </div>

</template>