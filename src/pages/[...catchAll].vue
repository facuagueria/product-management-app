<script setup lang="ts">
import AppErrorPage from '@/components/AppError/AppErrorPage.vue'

useErrorStore().setError({ error: 'Page Not Found', customCode: 404 })
</script>

<template>
  <div></div>
</template>
