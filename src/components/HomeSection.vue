<template>
  <section class="relative bg-cover bg-center text-white h-[400px] w-full" style="background-image: url(../../public/icon/mainHero.jpg);">
    <div class="absolute inset-0 bg-black/40 flex flex-col items-center justify-center px-4 text-center">
      <div class="w-[70%] flex flex-col justify-end items-start  ">
        <h1 class="text-4xl font-bold mb-4">Welcome.</h1>
        <p class="text-lg mb-6">Millions of movies, TV shows and people to discover. Explore now.</p>
        <div class="flex w-[90%] bg-white rounded-full overflow-hidden shadow">
          <input type="text" class="flex-grow px-7 py-2 text-gray-700 outline-none w-[70%]" placeholder="Search for a movie, tv show, person..." />
          <button class="bg-green-500 hover:bg-green-600 text-white px-6 py-2">Search</button>
        </div>
      </div>
    </div>
  </section>
</template>
<script setup lang="ts">
</script>