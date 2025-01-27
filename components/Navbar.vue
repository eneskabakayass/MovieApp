<script setup>
const moviesHover = ref(false);
const tvShowsHover = ref(false);
</script>
<template>
  <div id="app">
    <header class="flex justify-around   items-center px-6 py-4 bg-[#032540] text-white">
      <div class="flex items-center space-x-8">
        <img src="/icon/movieIcon.svg" class="w-44" />
        <nav class="flex space-x-6">
          <RouterLink to="/">Homepage</RouterLink>
          <div @mouseover="moviesHover= true; tvShowsHover= false" class="nav-link-item cursor-pointer">
            Movies
            <div v-show="moviesHover" @mouseleave="moviesHover = false" class="absolute z-20 under-link-container bg-white p-2 mt-2 text-slate-950 flex flex-col gap-2">
              <div class="under-link-item"><RouterLink to="/movie/popularPage">Popular</RouterLink></div>
              <div class="under-link-item"><RouterLink to="/movie/upcomingPage">Upcoming</RouterLink></div>
              <div class="under-link-item"><RouterLink to="/movie/topRatedPage">Top Rated</RouterLink></div>
            </div>
          </div>
          <div @mouseover="tvShowsHover= true; moviesHover= false" class="nav-link-item cursor-pointer">
            TV Shows
            <div v-show="tvShowsHover" @mouseleave="tvShowsHover = false" class="absolute z-20 under-link-container bg-white p-2 mt-2 text-slate-950 flex flex-col gap-2">
              <div class="under-link-item"><RouterLink to="/tvShow/popularPage">Popular</RouterLink></div>
              <div class="under-link-item"><RouterLink to="/tvShow/upcomingPage">Upcoming</RouterLink></div>
              <div class="under-link-item"><RouterLink to="/tvShow/topRatedPage">Top Rated</RouterLink></div>
            </div>
          </div>
        </nav>
      </div>

      <div class="flex items-center space-x-8">
        <img src="/icon/plus.svg" class="w-6" />
        <button class="border border-white rounded px-3 py-1">EN</button>
        <button class="hover:underline">Login</button>
        <button class="hover:underline">Join TMDB</button>
        <button>
          <img src="/icon/search.svg" class="w-6" />
        </button>
      </div>
    </header>
  </div>
</template>