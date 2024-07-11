<script setup lang="ts">
import OptionButton from './OptionButton.vue'
import IconCat from './icons/IconCat.vue'
import IconCatBlur from './icons/IconCatBlur.vue'
import IconCatPixel from './icons/IconCatPixel.vue'

import { ref } from 'vue'

const selectedOption = ref('None')

const emit = defineEmits(['update:selectedOption', 'sendFilterToHigherComponent'])

const updateSelectedFilter = (value) => {
  selectedOption.value = value
  emit('sendFilterToHigherComponent', value)
}
</script>

<template>
  <div class="flex flex-wrap gap-4 py-5">
    <OptionButton
      value="Blur"
      :selectedOption="selectedOption"
      @update:selectedOption="updateSelectedFilter"
    >
      <template #image>
        <div
          class="flex items-center justify-center p-2.5 w-[64px] h-[50px] border-[5px] border-inherit"
        >
          <div class="w-6 h-10">
            <IconCatBlur alt="Cat" class="text-inherit" />
          </div>
        </div>
      </template>

      Blur
    </OptionButton>

    <OptionButton
      value="Mono"
      :selectedOption="selectedOption"
      @update:selectedOption="updateSelectedFilter"
    >
      <template #image>
        <div
          class="flex items-center bg-white justify-center w-[64px] h-[50px] border-[5px] border-inherit"
        >
          <div class="w-5 h-10">
            <IconCat alt="Cat" class="text-black" />
          </div>
        </div>
      </template>
      Mono
    </OptionButton>

    <OptionButton
      value="Sepia"
      :selectedOption="selectedOption"
      @update:selectedOption="updateSelectedFilter"
    >
      <template #image>
        <div
          class="flex items-center justify-center bg-yellow-50 w-[64px] h-[50px] border-[5px] p-1 border-inherit"
        >
          <div class="w-5 h-10">
            <IconCat alt="Cat" class="text-yellow-400" />
          </div>
        </div>
      </template>
      Sepia
    </OptionButton>

    <OptionButton
      value="Negative"
      :selectedOption="selectedOption"
      @update:selectedOption="updateSelectedFilter"
    >
      <template #image>
        <div
          class="flex items-center bg-black justify-center w-[64px] h-[50px] border-[5px] p-2.5 border-inherit"
        >
          <div class="w-5 h-10">
            <IconCat alt="Cat" class="text-white" />
          </div>
        </div>
      </template>
      Negative
    </OptionButton>

    <OptionButton
      value="Paint"
      :selectedOption="selectedOption"
      @update:selectedOption="updateSelectedFilter"
    >
      <template #image>
        <div
          class="flex items-center justify-center bg-green-50 p-1 w-[64px] h-[50px] border-[5px] border-inherit"
        >
          <div class="w-5 h-10">
            <IconCat alt="Cat" class="text-green-600" />
          </div>
        </div>
      </template>
      Paint
    </OptionButton>

    <OptionButton
      value="Pixel"
      :selectedOption="selectedOption"
      @update:selectedOption="updateSelectedFilter"
    >
      <template #image>
        <div
          class="flex items-center justify-center p-1 w-[64px] h-[50px] border-[5px] border-inherit"
        >
          <div class="w-5 h-9">
            <IconCatPixel alt="Cat" class="text-inherit" />
          </div>
        </div>
      </template>
      Pixel
    </OptionButton>
  </div>
</template>
