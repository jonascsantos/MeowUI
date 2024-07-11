<script setup lang="ts">
import OptionAccordion from './OptionAccordion.vue'
import SizeOptions from './SizeOptions.vue'
import FilterOptions from './FilterOptions.vue'

import { ArrowsPointingOutIcon, PaintBrushIcon } from '@heroicons/vue/24/solid'

import { ref } from 'vue'

const receivedSize = ref({ value: '', label: 'Random' })
const receivedFilter = ref({ value: '', label: 'None' })

const typeQuery = ref(new URLSearchParams())

const emit = defineEmits(['update:searchParams'])

const handleSendSizeToHigherComponent = (Size) => {
  if (Size.value === 'Custom') {
    receivedSize.value.label = `${Size.width ? Size.width : 'Random'} x ${Size.height ? Size.height : 'Random'}`
    receivedSize.value.value = Size.value

    if (Size.width) {
      typeQuery.value.set('width', Size.width)
    }

    if (Size.height) {
      typeQuery.value.set('height', Size.height)
    }
  } else {
    receivedSize.value.value = Size.value
    receivedSize.value.label = Size.value
  }

  returnURL()
}

const handleSendFilterToHigherComponent = (Filter) => {
  switch (Filter.value) {
    case 'Blur':
      receivedFilter.value.label = `blur=${Filter.blur ?? 0}`
      break
    case 'Pixel':
      receivedFilter.value.label = `pixel=${Filter.pixel ?? 0}`
      break
    case 'Paint':
      receivedFilter.value.label = `r=${Filter.red || 0}&g=${Filter.green || 0}&b=${Filter.blue || 0}`
      break
    default:
      receivedFilter.value.label = Filter.value
      break
  }

  receivedFilter.value.value = Filter.value

  returnURL()
}

const returnURL = () => {
  let params = new URLSearchParams()

  const size = receivedSize.value.value.toLowerCase()
  const filter = receivedFilter.value.value.toLowerCase()

  let filterLabel = receivedFilter.value.label.toLowerCase()

  if (size !== 'random') {
    params.set('type', size)
  } else {
    params.delete('type')
  }

  if (filter) {
    params.set('filter', filter)
  }

  if (params.has('type', 'custom')) {
    params.delete('type')

    if (typeQuery.value.size) {
      params = new URLSearchParams({
        ...Object.fromEntries(params),
        ...Object.fromEntries(typeQuery.value)
      })
    }
  }

  if (
    filterLabel === 'mono' ||
    filterLabel === 'sepia' ||
    filterLabel === 'negative' ||
    filterLabel === 'none'
  ) {
    filterLabel = ''
  } else {
    filterLabel = '&' + filterLabel
  }

  emit('update:searchParams', params.toString() + filterLabel)
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
