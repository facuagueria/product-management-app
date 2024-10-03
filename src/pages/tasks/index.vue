<script setup lang="ts">
import { supabase, type Tables } from '@/lib/supabaseClient'
import { ref } from 'vue'

const tasks = ref<Tables<'tasks'>[] | null>(null)

const getTasks = async () => {
  const { data, error } = await supabase.from('tasks').select('*')

  if (error) console.log(error)

  tasks.value = data
}

;(async () => {
  await getTasks()
})()
</script>

<template>
  <div>
    <h1>Tasks Page</h1>
    <RouterLink to="/">Go to Home</RouterLink>
    <ul>
      <li v-for="task in tasks" :key="task.id">
        {{ task.name }}
      </li>
    </ul>
  </div>
</template>

<style scoped></style>
