<template>
  <Navbar />
  <Hero>
    <input type="text" placeholder="search" v-model="searchText" />
  </Hero>
  <div class="container section-filtered">
    <div class="row">
      <div class="col-12 col-lg-3">
        <div class="view-box">
          <a
            :class="`btn-view-type ${selectedFiltered.viewtype == view ? ' active ' : ''}`"
            v-for="view of viewType"
            @click.prevent="selectedFiltered.viewtype = view"
            >{{ view }}</a
          >
        </div>
      </div>
      <div class="col-12 col-lg-5">
        <div class="tab-buttons">
          <a
            :class="`tab-button ${selectedFiltered.filteredTab == tab ? 'active' : ''}`"
            v-for="tab of tabs"
            :key="tab"
            @click.prevent="selectedFiltered.filteredTab = tab"
          >
            {{ tab }}
          </a>
        </div>
      </div>
      <div class="col-12 col-lg-4">
        <div class="tools">
          <a
            :class="`btn-tools ${selectedFiltered.selectedTool == tool.name ? ' active ' : ''}`"
            v-for="tool of tools"
            :key="tool"
            @click.prevent="selectedFiltered.selectedTool = selectedFiltered.selectedTool == tool.name ? null : tool.name"
          >
            <img :src="`/${tool.path}`" :alt="tool.name" />
          </a>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
  import Navbar from "@/components/Navbar.vue";
  import Hero from "@/components/Hero.vue";
  import { ref, reactive } from "vue";
  import { data } from "./data";
  const searchText = ref("");
  const posts = data();

  const tools = reactive([
    { name: "figma", path: "figma.svg" },
    { name: "sketch", path: "sketch.svg" },
    { name: "indesign", path: "indesign.svg" },
    { name: "xd", path: "xd.svg" },
    { name: "ps", path: "ps.svg" },
  ]);
  const tabs = reactive(["all", "web", "mobile", "uı kit", "coded"]);
  const viewType = reactive(["lastest", "popular"]);

  const selectedFiltered = reactive({
    viewtype: "lastest",
    filteredTab: "all",
    selectedTool: null,
  });
</script>
