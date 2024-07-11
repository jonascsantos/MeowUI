<script setup lang="ts">
import OptionButton from './OptionButton.vue'
import { ArrowsPointingOutIcon } from '@heroicons/vue/24/solid'
import { PaintBrushIcon } from '@heroicons/vue/24/solid'
import IconCat from './icons/IconCat.vue'

import { ref } from 'vue'

const selectedFilter = ref('')

const updateSelectedFilter = (value) => {
  selectedFilter.value = value
}
</script>

<template>
  <div class="flex flex-wrap gap-4 py-5">
    <OptionButton :value="1" :modelValue="selectedFilter" @update:modelValue="updateSelectedFilter">
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

    <OptionButton :value="2" :modelValue="selectedFilter" @update:modelValue="updateSelectedFilter">
      <template #image>
        <div class="flex items-center justify-center w-[30px] h-[40px] border-[5px] border-inherit">
          <div class="w-4 h-10">
            <IconCat alt="Cat" class="text-inherit" />
          </div>
        </div>
      </template>
      Small
    </OptionButton>

    <OptionButton :value="3" :modelValue="selectedFilter" @update:modelValue="updateSelectedFilter">
      <template #image>
        <div class="flex items-center justify-center w-[30px] h-[40px] border-[5px] border-inherit">
          <div class="w-4 h-10">
            <IconCat alt="Cat" class="text-inherit" />
          </div>
        </div>
      </template>
      Medium
    </OptionButton>

    <OptionButton :value="4" :modelValue="selectedFilter" @update:modelValue="updateSelectedFilter">
      <template #image>
        <div class="flex items-center justify-center w-[30px] h-[40px] border-[5px] border-inherit">
          <div class="w-4 h-10">
            <IconCat alt="Cat" class="text-inherit" />
          </div>
        </div>
      </template>
      Square
    </OptionButton>

    <OptionButton :value="5" :modelValue="selectedFilter" @update:modelValue="updateSelectedFilter">
      <template #image>
        <div class="flex items-center justify-center w-[30px] h-[40px] border-[5px] border-inherit">
          <div class="w-4 h-10">
            <IconCat alt="Cat" class="text-inherit" />
          </div>
        </div>
      </template>
      Custom
    </OptionButton>
  </div>
</template>
