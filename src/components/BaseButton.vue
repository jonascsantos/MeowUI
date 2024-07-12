<script setup lang="ts">
type ButtonInstance = InstanceType<typeof Button>

const props = defineProps<{
  onClick: ButtonInstance['$props']['onClick']
}>()
</script>

<template>
  <div class="cursor-pointer rounded-full text-lg flex flex-col p-4 items-center" @click="onClick">
    <div class="font-medium">
      <slot></slot>
    </div>
  </div>
</template>
