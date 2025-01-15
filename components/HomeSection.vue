<script setup>
  import { ref, defineEmits } from 'vue';
  import lodash from 'lodash';
  const { debounce } = lodash;

  const emits = defineEmits(['update-search']);
  const searchTerm = ref('');

  const emitSearchTerm = debounce((term) =>{
    emits('update-search', term);
  }, 500);

  const updateSearchTerm = (event) => {
    searchTerm.value = event.target.value;

    if (searchTerm.value.length >= 3) {
      emitSearchTerm(searchTerm.value);
    } else if (searchTerm.value.length === 0) {
      emitSearchTerm('');
    }
  }
</script>
<template>
  <section class="relative bg-cover bg-center text-white h-[400px] w-full" style="background-image: url(/icon/mainHero.jpg);">
    <div class="absolute inset-0 bg-black/40 flex flex-col items-center justify-center px-4 text-center">
      <div class="w-full pl-72 pr-72">
        <div class="w-full flex flex-col items-start">
          <h1 class="text-4xl font-bold mb-4">Welcome.</h1>
          <p class="text-lg mb-6">Millions of movies, TV shows and people to discover. Explore now.</p>
        </div>
        <div class="flex w-full bg-white rounded-full overflow-hidden shadow">
          <input @input="updateSearchTerm" v-model="searchTerm" type="text" class="flex-grow px-5 py-2 text-gray-700 outline-none w-full h-12" placeholder="Search for a movie, tv show, person..." />
          <button class="bg-gradient-to-r from-[#1ed5a9] to-[#01b4e4] w-28 rounded-full h-[2.9rem] m-auto">Search</button>
        </div>
      </div>
    </div>
  </section>
</template>