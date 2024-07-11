<script setup lang="ts">
import OptionAccordion from './OptionAccordion.vue'
import SizeOptions from './SizeOptions.vue'
import { ArrowsPointingOutIcon } from '@heroicons/vue/24/solid'
import { PaintBrushIcon } from '@heroicons/vue/24/solid'
</script>

<template>
  <OptionAccordion>
    <template #icon>
      <ArrowsPointingOutIcon class="size-6 text-gray-900" />
    </template>
    <template #heading>
      <h3 class="font-bold">Size: <span class="font-bold text-fuchsia-700">Random</span></h3>
    </template>

    <SizeOptions />
  </OptionAccordion>

  <OptionAccordion>
    <template #icon>
      <PaintBrushIcon class="size-6 text-gray-900" />
    </template>
    <template #heading>
      <h3 class="font-bold">Filter: <span class="font-bold text-fuchsia-700">None</span></h3>
    </template>

    Content
  </OptionAccordion>
</template>
