<template>
  <div id="app">
    <NavBar />

    <main class="container pt-5 mt-4">
      <router-view />
    </main>

    <AppFooter />
  </div>
</template>


<script setup>
import NavBar from './components/common/NavBar.vue';
import AppFooter from './components/common/AppFooter.vue';
</script>

<style>
</style>

