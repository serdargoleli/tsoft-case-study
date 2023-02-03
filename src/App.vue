<template>
  <Navbar />
  <Hero>
    <input type="search" placeholder="Search designer name..." v-model="selectedFiltered.searchText" />
  </Hero>
  <div class="container section-filtered">
    <div class="row">
      <div class="col-12 col-lg-3">
        <div class="view-box">
          <a
            :class="`btn-view-type ${isActive(selectedFiltered.viewtype, view)}`"
            v-for="view of viewType"
            :key="view"
            @click.prevent="selectedFiltered.viewtype = selectedFiltered.viewtype == view ? null : view"
          >
            {{ view }}
          </a>
        </div>
      </div>
      <div class="col-12 col-lg-5">
        <div class="tab-buttons">
          <a
            :class="`tab-button  ${isActive(selectedFiltered.filteredTab, tab)}`"
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
            :class="`btn-tools ${isActive(selectedFiltered.selectedTool, tool.name)}`"
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

  <div class="container mt-5">
    <div class="row">
      <template v-if="filtredPosts.length > 0">
        <div class="col-12 col-md-6 col-lg-4" v-for="post of filtredPosts" :key="post.id">
          <PostCard :post="post" />
        </div>
      </template>
      <template v-else>
        <div class="col-12">
          <div class="alert alert-danger text-center">No posts found for the search criteria...</div>
        </div>
      </template>
    </div>
  </div>
</template>

<script setup>
  import Navbar from "@/components/Navbar.vue";
  import Hero from "@/components/Hero.vue";
  import PostCard from "@/components/PostCard.vue";
  import { ref, reactive, computed } from "vue";
  import { posts, tools, tabs, viewType } from "./data";

  const selectedFiltered = reactive({
    searchText: "",
    viewtype: null,
    filteredTab: "all",
    selectedTool: null,
  });

  const filtredPosts = computed(() => {
    let platform = selectedFiltered.filteredTab === "all" ? null : selectedFiltered.filteredTab;
    return posts
      .filter((post) => {
        return post.author.toLowerCase().includes(selectedFiltered.searchText.toLocaleLowerCase());
      })
      .filter((post) => {
        return selectedFiltered.viewtype == null || post.viewType.includes(selectedFiltered.viewtype);
      })
      .filter((post) => {
        return selectedFiltered.selectedTool == null || post.tool.includes(selectedFiltered.selectedTool);
      })
      .filter((post) => {
        return platform == null || post.type.includes(platform);
      });
  });

  const isActive = (selected, current) => {
    return selected === current ? " active " : null;
  };
</script>
