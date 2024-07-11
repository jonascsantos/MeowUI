<script setup lang="ts">
import { ref } from 'vue'

import OptionButton from './OptionButton.vue'
import IconCat from './icons/IconCat.vue'

const selectedOption = ref('Random')

const emit = defineEmits(['update:selectedOption', 'sendSizeToHigherComponent'])

const updateSelectedSize = (value) => {
  selectedOption.value = value
  emit('sendSizeToHigherComponent', value)
}
</script>

<template>
  <div class="flex flex-wrap gap-4 py-5">
    <OptionButton
      value="Random"
      :selectedOption="selectedOption"
      @update:selectedOption="updateSelectedSize"
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
      :selectedOption="selectedOption"
      @update:selectedOption="updateSelectedSize"
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
      :selectedOption="selectedOption"
      @update:selectedOption="updateSelectedSize"
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
      :selectedOption="selectedOption"
      @update:selectedOption="updateSelectedSize"
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
      :selectedOption="selectedOption"
      @update:selectedOption="updateSelectedSize"
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
