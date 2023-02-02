<template>
  <section class="hero">
    <h1 class="hero-title">Free UI resources for everyone</h1>
    <p class="hero-content">The largest database of 100% free UI components and designs available in the formats popular by UI designers.</p>
    <div class="hero-search-box">
      <div class="select-box">
        <button class="btn-modal">Free Design <ChevronDownIcon class="icon" /></button>
      </div>
      <div class="divider"></div>
      <div class="input-box">
        <MagnifyingGlassIcon class="icon" />
        <slot></slot>
      </div>
    </div>
  </section>
</template>

<script setup>
  import { MagnifyingGlassIcon, ChevronDownIcon } from "@heroicons/vue/24/solid";
</script>
