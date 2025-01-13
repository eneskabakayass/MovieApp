<script>
import '@/assets/tailwind.css';
import {defineComponent} from "vue";
import Navbar from "@/components/Navbar.vue";
import HomeSection from "@/components/HomeSection.vue";
import RecommenderItem from "@/components/RecommenderItem.vue";

export default defineComponent({
  components: {RecommenderItem, HomeSection, Navbar}
})

</script>

<template>
  <div>
    <Navbar />
    <HomeSection />
    <RecommenderItem />
  </div>
</template>
