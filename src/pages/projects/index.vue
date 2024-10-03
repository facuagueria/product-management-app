<script setup lang="ts">
import { supabase, type Tables } from '@/lib/supabaseClient'
import { ref } from 'vue'

const projects = ref<Tables<'projects'>[] | null>(null)

const getProjects = async () => {
  const { data, error } = await supabase.from('projects').select('*')

  if (error) console.log(error)

  projects.value = data
}

;(async () => {
  await getProjects()
})()
</script>

<template>
  <div>
    <h1>Projects Page</h1>
    <RouterLink to="/">Go to Home</RouterLink>
    <ul>
      <li v-for="project in projects" :key="project.id">
        {{ project.name }}
      </li>
    </ul>
  </div>
</template>

<style scoped></style>
