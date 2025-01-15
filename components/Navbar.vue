<template>
  <div id="app">
    <header class="flex justify-around   items-center px-6 py-4 bg-[#032540] text-white">
      <div class="flex items-center space-x-8">
        <img src="/icon/movieIcon.svg" class="w-44" />
        <nav class="flex space-x-6">
          <button class="hover:underline">Movies</button>
          <button class="hover:underline">TV Shows</button>
          <button class="hover:underline">People</button>
          <button class="hover:underline">More</button>
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