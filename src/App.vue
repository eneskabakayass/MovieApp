<script>
import './assets/tailwind.css';
import {defineComponent} from "vue";
import Navbar from "@/components/Navbar.vue";
import HomeSection from "@/components/HomeSection.vue";

export default defineComponent({
  components: {HomeSection, Navbar}
})

</script>

<template>
  <div>
    <Navbar />
    <HomeSection />
  </div>
</template>
