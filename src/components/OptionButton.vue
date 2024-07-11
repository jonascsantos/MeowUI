<script setup lang="ts">
import { computed } from 'vue'

import { ChevronDownIcon } from '@heroicons/vue/24/solid'

const props = defineProps({
  value: {
    type: String,
    required: true
  },
  selectedFilter: {
    type: String,
    required: true
  }
})

const isSelected = computed(() => props.selectedFilter === props.value)

const emit = defineEmits(['update:selectedFilter'])

const selectFilter = () => {
  emit('update:selectedFilter', props.value)
}
</script>

<template>
  <div
    :class="[isSelected ? 'border-fuchsia-700 bg-fuchsia-50' : 'border-gray-300']"
    class="border-4 w-[100px] h-[120px] rounded-lg flex flex-col p-4 gap-2.5 items-center"
    @click="selectFilter"
  >
    <div class="font-medium" :class="[isSelected ? 'text-fuchsia-700' : 'text-gray-400']">
      <slot></slot>
    </div>

    <div
      :class="[
        isSelected ? 'text-fuchsia-700 border-fuchsia-700' : 'border-gray-300 text-gray-300'
      ]"
      class="items-center"
    >
      <slot name="image"></slot>
    </div>
  </div>
</template>
