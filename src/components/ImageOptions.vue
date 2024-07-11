<script setup lang="ts">
import OptionAccordion from './OptionAccordion.vue'
import SizeOptions from './SizeOptions.vue'
import FilterOptions from './FilterOptions.vue'

import { ArrowsPointingOutIcon, PaintBrushIcon } from '@heroicons/vue/24/solid'

import { ref } from 'vue'

const receivedSize = ref('Random')
const receivedFilter = ref('None')

const handleSendSizeToHigherComponent = (Size) => {
  receivedSize.value = Size
}

const handleSendFilterToHigherComponent = (Filter) => {
  receivedFilter.value = Filter
}
</script>

<template>
  <OptionAccordion>
    <template #icon>
      <ArrowsPointingOutIcon class="size-6 text-gray-900" />
    </template>
    <template #heading>
      <h3 class="font-bold">
        Size: <span class="font-bold text-fuchsia-700">{{ receivedSize }}</span>
      </h3>
    </template>

    <SizeOptions @sendSizeToHigherComponent="handleSendSizeToHigherComponent" />
  </OptionAccordion>

  <OptionAccordion>
    <template #icon>
      <PaintBrushIcon class="size-6 text-gray-900" />
    </template>
    <template #heading>
      <h3 class="font-bold">
        Filter: <span class="font-bold text-fuchsia-700">{{ receivedFilter }}</span>
      </h3>
    </template>

    <FilterOptions @sendFilterToHigherComponent="handleSendFilterToHigherComponent" />
  </OptionAccordion>
</template>
