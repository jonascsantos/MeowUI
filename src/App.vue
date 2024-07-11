<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import NavigationBar from './components/NavigationBar.vue'
</script>

<template>
  <div class="2xl:px-16 max-w-[2200px] m-auto">
    <header>
      <div class="wrapper">
        <NavigationBar />
      </div>
    </header>

    <RouterView />
  </div>
</template>
