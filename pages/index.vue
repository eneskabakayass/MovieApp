<template>
  <div>
    <Navbar/>
    <HomeSection @update-search="handleSearch"/>
    <RecommenderItem :search-term="searchTerm"/>
  </div>
</template>