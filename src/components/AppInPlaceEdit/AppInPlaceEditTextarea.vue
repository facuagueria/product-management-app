<script setup lang="ts">
const value = defineModel<string>()

defineEmits(['commit'])
</script>

<template>
  <textarea
    v-model="value"
    class="w-full bg-transparent p-1 focus:rounded-md focus:border-none focus:bg-gray-800 focus:outline-none"
    @blur="$emit('commit')"
  />
</template>
