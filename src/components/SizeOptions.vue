<script setup lang="ts">
import { ref, watch } from 'vue'

import OptionButton from './OptionButton.vue'
import IconCat from './icons/IconCat.vue'

const selectedOption = ref('Random')

const width = ref<string | number>('')
const height = ref<string | number>('')
const showCustomSize = ref(false)

const emit = defineEmits(['update:selectedOption', 'sendSizeToHigherComponent'])

const updateSelectedSize = (value: string) => {
  selectedOption.value = value
  emit('update:selectedOption', value)
  emit('sendSizeToHigherComponent', { value: selectedOption.value })

  if (value === 'Custom') {
    showCustomSize.value = true
  } else {
    showCustomSize.value = false
  }
}

watch([width, height], ([newWidth, newHeight]) => {
  emit('sendSizeToHigherComponent', {
    value: selectedOption.value,
    width: newWidth,
    height: newHeight
  })
})
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
  <div v-if="showCustomSize" class="flex gap-4 sm:max-w-full md:max-w-[400px]">
    <div class="w-50">
      <label for="Width" class="block text-sm leading-6 text-gray-900 font-bold">Width</label>
      <div class="relative mt-2 rounded-md shadow-sm">
        <input
          v-model="width"
          type="number"
          name="Width"
          min="0"
          max="3000"
          pattern="[0-9]{4}"
          id="Width"
          class="block w-full outline-none rounded-md border-0 py-1.5 pl-3 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-fuchsia-700 sm:text-sm sm:leading-6"
          placeholder="1280"
        />
      </div>
    </div>

    <div class="w-50">
      <label for="Height" class="block text-sm leading-6 text-gray-900 font-bold">Height</label>
      <div class="relative mt-2 rounded-md shadow-sm">
        <input
          v-model="height"
          type="number"
          name="Height"
          min="0"
          max="3000"
          pattern="[0-9]{4}"
          id="Height"
          class="block w-full outline-none rounded-md border-0 py-1.5 pl-3 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-fuchsia-700 sm:text-sm sm:leading-6"
          placeholder="720"
        />
      </div>
    </div>
  </div>
</template>
