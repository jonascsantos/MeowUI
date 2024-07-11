<script setup lang="ts">
import ImageOptions from '../components/ImageOptions.vue'
import BaseButton from '../components/BaseButton.vue'

const onClick = () => {
  console.log('clicked!')
}
</script>

<template>
  <main class="text-gray-900 flex grid gap-6">
    <div class="px-4">
      <h2 class="text-base py-4">Fetch random cat images from <b>cataas.com</b></h2>
      <ImageOptions />

      <div class="sticky bottom-0 py-4">
        <BaseButton :onClick="onClick">Fetch from API 🐈</BaseButton>
      </div>
    </div>
  </main>
</template>
