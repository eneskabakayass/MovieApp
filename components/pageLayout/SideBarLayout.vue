<script setup>
import { ref, watch } from 'vue';

const props = defineProps({
  pageTitle: String,
  selectedSort: String,
  selectedFilter: String,
  genres: Object
});

const emit = defineEmits(['update-sort', 'update-filter']);
const sortValue = ref(props.selectedSort);
const filterValue = ref(props.selectedFilter);

watch(sortValue, (newVal) => {
  emit('update-sort', newVal);
});

watch(filterValue, (newVal) => {
  emit('update-filter', newVal);
});

// Destructure props for easy access in template
const { pageTitle, genres } = props;
</script>

<template>
  <div class="bar-wrapper flex flex-col p-5 gap-5 w-10 flex-1">
    <div class="title">{{ pageTitle }}</div>
    <div class="sort-container p-5 flex flex-col gap-2">
      <div class="title">Sort</div>
      <hr />
      <span>Sort Results By</span>
      <select v-model="sortValue" class="p-2" name="sorting">
        <option value="desc">Popularity Descending</option>
        <option value="asc">Popularity Ascending</option>
      </select>
    </div>
    <div class="filter-container p-5 flex flex-col gap-2">
      <div class="title">Filter</div>
      <hr />
      <span>Filter Results By</span>
      <select v-model="filterValue" class="p-2" name="genre">
        <option :value="genres.action">Action Genre</option>
        <option :value="genres.comedy">Comedy Genre</option>
      </select>
    </div>
  </div>
</template>

<style>
.bar-wrapper .title {
  white-space: nowrap;
  font-size: 22px;
}

.bar-wrapper .sort-container,
.bar-wrapper .filter-container {
  border: 2px solid gray;
  border-radius: 8px;
  box-shadow: 10px 10px 10px rgba(0, 0, 0, 0.1);
}

.bar-wrapper .sort-container select,
.bar-wrapper .filter-container select {
  background: #ccc;
  border-radius: 6px;
  cursor: pointer;
}

.content-wrapper {
  flex: 3;
}

.content-wrapper .rating {
  width: fit-content;
}

.content-wrapper .title {
  width: 200px;
}
</style>
