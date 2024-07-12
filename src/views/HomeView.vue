<script setup lang="ts">
import { ref } from 'vue'

import ImageOptions from '../components/ImageOptions.vue'
import BaseButton from '../components/BaseButton.vue'

import { ArrowUturnLeftIcon } from '@heroicons/vue/24/solid'

const queryUrl = ref(new URL(import.meta.env.VITE_APP_BASE_URL))
const fetchUrl = ref()
const imageRef = ref(null)
const showImage = ref(false)

const fetchImage = () => {
  fetchUrl.value = queryUrl.value

  const timestamp = Date.now()

  fetchUrl.value.searchParams.set('timestamp', timestamp)

  if (imageRef.value) {
    imageRef.value.src = fetchUrl.value
  }
}

const hideImage = () => {
  showImage.value = false
}

const onClick = () => {
  showImage.value = true
  if (showImage.value) {
    fetchImage()
  }
}

const updateSearchParams = (searchParams) => {
  queryUrl.value.search = new URLSearchParams(searchParams)
}
</script>

<template>
  <main class="md:flex text-gray-900 flex grid gap-6 min-h-screen">
    <div class="md:w-1/3 px-4">
      <h2 class="text-base py-4">Fetch random cat images from <b>cataas.com</b></h2>
      <ImageOptions @update:searchParams="updateSearchParams" />

      <div class="sticky bottom-0 py-8">
        <BaseButton class="bg-fuchsia-700 text-white" :onClick="onClick"
          >Fetch from API 🐈</BaseButton
        >
      </div>
    </div>
    <div
      class="min-h-screen sm:translate-x-0 absolute sm:relative bottom-0 top-0 left-0 right-0 md:w-2/3 transition-all"
      :class="[showImage ? 'translate-x-0' : 'translate-x-full']"
    >
      <div class="flex h-full relative w-full bg-fuchsia-700 justify-center items-center">
        <div class="flex justify-center items-center">
          <img v-show="fetchUrl" ref="imageRef" class="h-min w-5/6" cache="false" src="" />
        </div>

        <div class="sm:hidden absolute bottom-20 left-10 right-10">
          <BaseButton class="bg-white text-gray-900 w-[310px]" :onClick="onClick">
            Give me another cat 🐱
          </BaseButton>
        </div>

        <div class="sm:hidden absolute bottom-1/2 left-[-40px]">
          <div
            class="rounded-full text-lg flex pl-[50px] pr-[12px] items-center bg-white text-gray-900 w-[85px] h-[100px]"
            :onClick="hideImage"
          >
            <ArrowUturnLeftIcon class="size-5 text-gray-900" />
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
