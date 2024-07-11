<script setup lang="ts">
import OptionButton from './OptionButton.vue'
import IconCat from './icons/IconCat.vue'
import IconCatBlur from './icons/IconCatBlur.vue'
import IconCatPixel from './icons/IconCatPixel.vue'

import { ref, watch } from 'vue'

const selectedOption = ref('None')

const emit = defineEmits(['update:selectedOption', 'sendFilterToHigherComponent'])

const blur = ref<string | number>('')
const pixel = ref<string | number>('')

const red = ref<string | number>('')
const green = ref<string | number>('')
const blue = ref<string | number>('')

const showBlurInput = ref(false)
const showPixelInput = ref(false)
const showPaintInputs = ref(false)

const updateSelectedFilter = (value: string) => {
  selectedOption.value = value
  emit('update:selectedOption', value)
  emit('sendFilterToHigherComponent', { value: selectedOption.value })

  showBlurInput.value = value === 'Blur'
  showPaintInputs.value = value === 'Paint'
  showPixelInput.value = value === 'Pixel'
}

watch([red, green, blue], ([newRed, newGreen, newBlue]) => {
  emit('sendFilterToHigherComponent', {
    value: selectedOption.value,
    red: newRed,
    green: newGreen,
    blue: newBlue
  })
})

watch([blur], ([newBlur]) => {
  emit('sendFilterToHigherComponent', {
    value: selectedOption.value,
    blur: newBlur
  })
})

watch([pixel], ([newPixel]) => {
  emit('sendFilterToHigherComponent', {
    value: selectedOption.value,
    pixel: newPixel
  })
})

const clearInputs = () => {
  blur.value = ''
  pixel.value = ''
  red.value = ''
  green.value = ''
  blue.value = ''
}
</script>

<template>
  <div class="flex flex-wrap gap-4 py-5">
    <OptionButton
      value="Blur"
      :selectedOption="selectedOption"
      @update:selectedOption="updateSelectedFilter"
      @click="clearInputs"
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
      @click="clearInputs"
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
      @click="clearInputs"
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
      @click="clearInputs"
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
      @click="clearInputs"
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
      @click="clearInputs"
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

  <div>
    <div v-if="showBlurInput" class="flex gap-4 max-w-[100px]">
      <div class="w-50">
        <label for="Blur" class="block text-sm leading-6 text-gray-900 font-bold">Blur</label>
        <div class="relative mt-2 rounded-md shadow-sm">
          <input
            v-model="blur"
            type="number"
            name="Blur"
            min="0"
            id="Blur"
            class="block w-full outline-none rounded-md border-0 py-1.5 pl-3 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-fuchsia-700 sm:text-sm sm:leading-6"
            placeholder="10"
          />
        </div>
      </div>
    </div>

    <div v-if="showPixelInput" class="flex gap-4 max-w-[100px]">
      <div class="w-50">
        <label for="Pixel" class="block text-sm leading-6 text-gray-900 font-bold">Pixel</label>
        <div class="relative mt-2 rounded-md shadow-sm">
          <input
            v-model="pixel"
            type="number"
            name="Pixel"
            min="0"
            id="Pixel"
            class="block w-full outline-none rounded-md border-0 py-1.5 pl-3 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-fuchsia-700 sm:text-sm sm:leading-6"
            placeholder="10"
          />
        </div>
      </div>
    </div>

    <div v-if="showPaintInputs" class="flex gap-4 sm:max-w-full md:max-w-[400px]">
      <div class="w-50">
        <label for="Red" class="block text-sm leading-6 text-gray-900 font-bold">Red</label>
        <div class="relative mt-2 rounded-md shadow-sm">
          <input
            v-model="red"
            type="number"
            name="Red"
            min="0"
            max="255"
            pattern="[0-9]"
            id="Red"
            class="block w-full outline-none rounded-md border-0 py-1.5 pl-3 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-fuchsia-700 sm:text-sm sm:leading-6"
            placeholder="0"
          />
        </div>
      </div>

      <div class="w-50">
        <label for="Green" class="block text-sm leading-6 text-gray-900 font-bold">Green</label>
        <div class="relative mt-2 rounded-md shadow-sm">
          <input
            v-model="green"
            type="number"
            name="Green"
            min="0"
            max="3000"
            pattern="[0-9]{4}"
            id="Green"
            class="block w-full outline-none rounded-md border-0 py-1.5 pl-3 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-fuchsia-700 sm:text-sm sm:leading-6"
            placeholder="150"
          />
        </div>
      </div>

      <div class="w-50">
        <label for="Blue" class="block text-sm leading-6 text-gray-900 font-bold">Blue</label>
        <div class="relative mt-2 rounded-md shadow-sm">
          <input
            v-model="blue"
            type="number"
            name="Blue"
            min="0"
            max="3000"
            pattern="[0-9]{4}"
            id="Blue"
            class="block w-full outline-none rounded-md border-0 py-1.5 pl-3 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-fuchsia-700 sm:text-sm sm:leading-6"
            placeholder="255"
          />
        </div>
      </div>
    </div>
  </div>
</template>
