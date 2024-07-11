<script setup lang="ts">
import { ref } from 'vue'

import { ChevronDownIcon } from '@heroicons/vue/24/solid'

const isOpen = ref(true)

const toggle = () => {
  isOpen.value = !isOpen.value
}
</script>

<template>
  <div class="accordion overflow-hidden">
    <div
      @click="toggle"
      class="header flex justify-space-between items-center p-2.5 cursor-pointer border-b border-gray-200"
    >
      <div class="flex-1 w-100 flex gap-2.5 items-center">
        <i>
          <slot name="icon"></slot>
        </i>

        <div>
          <slot name="heading"></slot>
        </div>
      </div>

      <i>
        <ChevronDownIcon
          :class="{ 'transform rotate-180': isOpen }"
          class="transition-transform size-5 text-gray-900"
        />
      </i>
    </div>

    <div :class="{ 'max-h-[40rem]': isOpen }" class="content max-h-0 h-max transition-maxHeight">
      <slot></slot>
    </div>
  </div>
</template>
