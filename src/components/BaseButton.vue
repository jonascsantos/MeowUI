<script setup lang="ts">
type ButtonInstance = InstanceType<typeof Button>

const props = defineProps<{
  onClick: ButtonInstance['$props']['onClick']
  isLoading: Boolean
}>()
</script>

<template>
  <div
    class="border-4 w-[100px] h-[120px] rounded-lg flex flex-col p-4 gap-2.5 items-center"
    @click="onClick"
  >
    <div class="font-medium">
      <slot></slot>
    </div>
  </div>
</template>
