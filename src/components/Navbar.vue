<template>
  <header class="header">
    <div class="container">
      <div class="row">
        <div class="col-6 col-lg-2">
          <div class="logo">
            <img src="/logo.svg" alt="" />
          </div>
        </div>
        <div class="col-6 d-flex justify-content-end d-lg-none">
          <div class="mobil-button-box">
            <button class="btn-open-menu" @click="menuToggle"><Bars3Icon class="icon" /></button>
          </div>
        </div>
        <div class="overlay" @click="menuToggle" v-if="isOpenMobileMenu"></div>
        <div class="col-lg-7">
          <nav :class="`menu ${isOpenMobileMenu ? 'mobile-menu-show' : ''}`">
            <a class="btn-close-menu" @click.prevent="menuToggle"> <XMarkIcon class="icon" /> </a>
            <a href="#" class="menu-item active">Free Design</a>
            <a href="#" class="menu-item">Lisance</a>
            <a href="#" class="menu-item">Articles</a>
            <a href="#" class="menu-item">Contributors</a>
            <a href="#" class="menu-item">About</a>
          </nav>
        </div>
        <div class="col-lg-3">
          <div class="buttons">
            <button class="button btn-ghost me-1">Login</button>
            <button class="button btn-primary">Sign Up</button>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>

<script setup>
  import { ref } from "vue";
  import { Bars3Icon, XMarkIcon } from "@heroicons/vue/24/solid";
  const isOpenMobileMenu = ref(false);

  const menuToggle = () => {
    isOpenMobileMenu.value = !isOpenMobileMenu.value;
  };
</script>
