<script>
import MovieContentView from '../../components/pageLayout/movieDetail.vue';
import { useStore } from '../../stores/store.js';

export default {
  components: {
    MovieContentView
  },
  data() {
    const store = useStore();
    const route = useRoute();
    const isFavorite = computed(() => store.isFavorite(movie));
    const movie = route.query.movie ? JSON.parse(route.query.movie) : {};

    console.log(movie)

    const toggleFavorite = () => {
      store.toggleFavorite(movie);
    };

    return {
      movie: {},
      actors: [],
      toggleFavorite,
      isFavorite
    };
  },
  created() {
    const route = useRoute();
    const movieData = route.query.movie ? JSON.parse(route.query.movie) : {};

    this.movie = movieData;
    this.actors = movieData.actors || [];
  },
  computed: {
    formattedVoteAverage() {
      return this.movie.vote_average?.toFixed(1);
    }
  },
  methods: {
    getImageUrl(path) {
      return `https://image.tmdb.org/t/p/w500${path}`;
    }
  }
};
</script>

<template>
  <Navbar/>
  <MovieContentView>
      <div class="content-wrapper flex flex-row gap-4 p-10">
        <img :src="getImageUrl(movie.poster_path)" alt="Poster">
        <div class="information">
          <div class="mb-4 mt-10 text-3xl">{{ movie.title }} ({{ movie.release_date }})</div>
          <div class="rate-container flex items-center gap-2 mb-4">
            <div class="flex justify-center items-center w-10 h-10 p-2 rounded-full border-4 border-[#20c774] z-10 top-56 left-5 leading-none text-center text-xs font-bold text-white bg-[#081c21]">
              {{ formattedVoteAverage }}
            </div>
            <button @click.stop="toggleFavorite" class="flex items-center justify-center w-10 h-10 bg-red-50 rounded-full">
              <i :class="isFavorite ? 'pi pi-star text-yellow-500' : 'pi pi-star text-gray-400'" class="text-xl"></i>
            </button>
          </div>
          <div>
            <span class="text-xl">Overview</span>
            <div>{{ movie.overview }}</div>
          </div>
        </div>
      </div>
    <RecommenderItem class="!content-start pl-10 !mt-0"/>
  </MovieContentView>
</template>
