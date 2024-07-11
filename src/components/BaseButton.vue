<script setup lang="ts">
type ButtonInstance = InstanceType<typeof Button>

const props = defineProps<{
  onClick: ButtonInstance['$props']['onClick']
  isLoading: Boolean
}>()
</script>

<template>
  <div class="rounded-full text-lg flex flex-col p-4 items-center" @click="onClick">
    <div class="font-medium">
      <slot></slot>
    </div>
  </div>
</template>
