<script setup>

</script>

<template>
  <div class="text-base sm:text-2xl">
    <div ref="dark" class="">
      <div @click="$refs.dark.classList.toggle('dark')">
      <div class="min-h-screen bg-gradient-to-br from-emerald-950 to-indigo-950 text-teal-100 dark:bg-gradient-to-br dark:from-yellow-300 dark:to-red-500 "> 
        <div class="text-6xl text-center py-5">Pozdrav, ja sam <span class="text-cyan-400">Luka Catela</span></div>
        <div class="w-[1034px] border-2 opacity-75 rounded-full mx-auto my-5"></div>

        <div class="text-2xl text-teal-100/75 max-w-[1034px] mx-auto pl-3 my-5">Moji omiljeni filmovi:</div>

        <div class="flex justify-center items-center py-5">
          <div class="flex flex-col items-center px-3">
            <img src="./assets/img1.jpg" class="w-[320px] h-[480px] rounded-md">
            <span class="text-2xl py-5">Oppenheimer</span>
          </div>
          <div class="flex flex-col items-center px-3">
            <img src="./assets/img2.jpg" class="w-[320px] h-[480px] rounded-md">
            <span class="text-2xl py-5">Interstelar</span>
          </div>
          <div class="flex flex-col items-center px-3">
            <img src="./assets/img3.jpg" class="w-[320px] h-[480px] rounded-md">
            <span class="text-2xl py-5">Gladiator</span>
          </div>
        </div>
      </div>
      </div>
    </div>
  </div>
</template>


<style scoped>

</style>
