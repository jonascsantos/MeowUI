<script setup lang="ts">
import OptionAccordion from './OptionAccordion.vue'
import SizeOptions from './SizeOptions.vue'
import FilterOptions from './FilterOptions.vue'

import { ArrowsPointingOutIcon, PaintBrushIcon } from '@heroicons/vue/24/solid'

import { ref } from 'vue'

const receivedSize = ref({ value: '', label: 'Random' })
const receivedFilter = ref({ value: '', label: 'None' })

const handleSendSizeToHigherComponent = (Size) => {
  if (Size.value === 'Custom') {
    receivedSize.value.label = `${Size.width ? Size.width : 'Random'} x ${Size.height ? Size.height : 'Random'}`
    receivedSize.value.value = Size.value
  } else {
    receivedSize.value.value = Size.value
    receivedSize.value.label = Size.value
  }
}

const handleSendFilterToHigherComponent = (Filter) => {
  switch (Filter.value) {
    case 'Blur':
      receivedFilter.value.label = `Blur: ${Filter.blur ?? 0}`
      receivedFilter.value.value = Filter.blur ?? 0
      break
    case 'Pixel':
      receivedFilter.value.label = `Pixel: ${Filter.pixel ?? 0}`
      receivedFilter.value.value = Filter.pixel ?? 0
      break
    case 'Paint':
      console.log(Filter)
      receivedFilter.value.label = `Red: ${Filter.red || 0}, Green: ${Filter.green || 0}, Blue: ${Filter.blue || 0}`
      receivedFilter.value.value = `${Filter.red ?? 0},${Filter.green ?? 0},${Filter.blue ?? 0}`
      break
    default:
      receivedFilter.value.label = Filter.value
      receivedFilter.value.value = Filter.value
      break
  }
}
</script>

<template>
  <OptionAccordion>
    <template #icon>
      <ArrowsPointingOutIcon class="size-6 text-gray-900" />
    </template>
    <template #heading>
      <h3 class="font-bold">
        Size: <span class="font-bold text-fuchsia-700">{{ receivedSize.label }}</span>
      </h3>
    </template>

    <div class="pb-4">
      <SizeOptions @sendSizeToHigherComponent="handleSendSizeToHigherComponent" />
    </div>
  </OptionAccordion>

  <OptionAccordion>
    <template #icon>
      <PaintBrushIcon class="size-6 text-gray-900" />
    </template>
    <template #heading>
      <h3 class="font-bold">
        Filter: <span class="font-bold text-fuchsia-700">{{ receivedFilter.label }}</span>
      </h3>
    </template>

    <div class="pb-4">
      <FilterOptions @sendFilterToHigherComponent="handleSendFilterToHigherComponent" />
    </div>
  </OptionAccordion>
</template>
