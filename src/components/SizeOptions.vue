<script setup lang="ts">
import OptionButton from './OptionButton.vue'
import { ArrowsPointingOutIcon } from '@heroicons/vue/24/solid'
import { PaintBrushIcon } from '@heroicons/vue/24/solid'
import IconCat from './icons/IconCat.vue'

import { ref } from 'vue'

const selectedFilter = ref('Random')

const emit = defineEmits(['update:selectedFilter', 'sendToHigherComponent'])

const updateSelectedFilter = (value) => {
  selectedFilter.value = value
  emit('sendToHigherComponent', value)
}
</script>

<template>
  <div class="flex flex-wrap gap-4 py-5">
    <OptionButton
      value="Random"
      :selectedFilter="selectedFilter"
      @update:selectedFilter="updateSelectedFilter"
    >
      <template #image>
        <div
          class="flex items-center justify-center p-2.5 w-[64px] h-[50px] border-[5px] border-inherit"
        >
          <div class="w-6 h-10">
            <IconCat alt="Cat" class="text-inherit" />
          </div>
        </div>
      </template>

      Random
    </OptionButton>

    <OptionButton
      value="Small"
      :selectedFilter="selectedFilter"
      @update:selectedFilter="updateSelectedFilter"
    >
      <template #image>
        <div class="flex items-center justify-center w-[30px] h-[40px] border-[5px] border-inherit">
          <div class="w-4 h-10">
            <IconCat alt="Cat" class="text-inherit" />
          </div>
        </div>
      </template>
      Small
    </OptionButton>

    <OptionButton
      value="Medium"
      :selectedFilter="selectedFilter"
      @update:selectedFilter="updateSelectedFilter"
    >
      <template #image>
        <div
          class="flex items-center justify-center w-[40px] h-[50px] border-[5px] p-1 border-inherit"
        >
          <div class="w-6 h-12">
            <IconCat alt="Cat" class="text-inherit" />
          </div>
        </div>
      </template>
      Medium
    </OptionButton>

    <OptionButton
      value="Square"
      :selectedFilter="selectedFilter"
      @update:selectedFilter="updateSelectedFilter"
    >
      <template #image>
        <div
          class="flex items-center justify-center w-[50px] h-[50px] border-[5px] p-2.5 border-inherit"
        >
          <div class="w-6 h-10">
            <IconCat alt="Cat" class="text-inherit" />
          </div>
        </div>
      </template>
      Square
    </OptionButton>

    <OptionButton
      value="Custom"
      :selectedFilter="selectedFilter"
      @update:selectedFilter="updateSelectedFilter"
    >
      <template #image>
        <div
          class="flex items-center justify-center p-1 w-[64px] h-[40px] border-[5px] border-inherit"
        >
          <div class="w-4 h-10">
            <IconCat alt="Cat" class="text-inherit" />
          </div>
        </div>
      </template>
      Custom
    </OptionButton>
  </div>
</template>
