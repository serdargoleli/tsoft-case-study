<template>
  <div class="post-card">
    <div class="post-card-tool">
      <img :src="`/${post.tool}.svg`" />
    </div>
    <div class="post-card-image">
      <img :src="post.image" alt="" />
    </div>
    <div class="post-card-footer">
      <div class="post-card-footer-left">
        <img class="author-image" :src="post.profile" alt="" />
        <h3 class="author-name">
          by <span>{{ post.author }}</span>
        </h3>
      </div>
      <div class="post-card-footer-right">
        <div class="icon-box me-2">
          <CodeBracketIcon class="icon" />
          <span> {{ post.hits }} </span>
        </div>
        <div class="icon-box">
          <img class="icon" src="/like.svg" alt="" />
          <span>{{ post.like }} </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
  import { CodeBracketIcon } from "@heroicons/vue/24/outline";
  defineProps(["post"]);
</script>
