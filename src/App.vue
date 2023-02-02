<template>
  <Navbar />
  <Hero>
    <input type="text" placeholder="search" v-model="searchText" />
  </Hero>
</template>
<script setup>
  import Navbar from "@/components/Navbar.vue";
  import Hero from "@/components/Hero.vue";
  import { ref, reactive } from "vue";
  import { data } from "./data";
  const searchText = ref("");
  const posts = data();
  console.log(posts);
</script>
