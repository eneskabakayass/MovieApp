<template>
  <div class="border-gray-50">
    <Navbar/>
    <HomeSection @update-search="handleSearch"/>
    <RecommenderItem :search-term="searchTerm"/>
  </div>
</template>
