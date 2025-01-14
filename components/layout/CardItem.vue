<script>
import { useStore } from '~/stores/store.js';
import { computed, defineComponent } from 'vue';

export default defineComponent({
  props: {
    movie: {
      type: Object,
      required: true,
    },
  },
  setup(props) {
    const store = useStore();

    const isFavorite = computed(() => store.isFavorite(props.movie));

    const toggleFavorite = () => {
      store.toggleFavorite(props.movie);
    };

    const getImageUrl = () => {
      return `https://image.tmdb.org/t/p/w220_and_h330_face/${props.movie.poster_path}`;
    };

    return { isFavorite, toggleFavorite, getImageUrl };
  },
});
</script>

<template>
  <div class="w-44 h-full mt-6 p-2 relative">
    <img class="w-full h-auto rounded-xl mb-4 object-cover" :src="getImageUrl()" :alt="`Poster of ${movie.title}`" />
    <div class="flex justify-center items-center w-10 h-10 absolute p-2 rounded-full border-4 border-[#20c774] z-10 top-56 left-5 leading-none text-center text-xs font-bold text-white bg-[#081c21]">
      {{ movie.vote_average.toFixed(1) }}
    </div>
    <div class="text-left text-lg font-semibold text-gray-800">
      {{ movie.title }}
    </div>
    <div class="text-left text-sm text-gray-500">
      {{ movie.release_date }}
    </div>
    <button @click.stop="toggleFavorite" class="absolute top-[-30px] right-1 flex items-center justify-center mt-4 mx-auto w-10 h-10 bg-red-50 rounded-full">
      <i :class="isFavorite ? 'pi pi-star text-yellow-500' : 'pi pi-star text-gray-400'" class="text-xl"></i>
    </button>
  </div>
</template>