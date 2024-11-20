<script setup lang="ts">
import { columns } from '@/utils/table-columns/projectsColumns'

usePageStore().pageData.title = 'Projects'

//Projects
const projectsLoader = useProjectsStore()
const { projects } = storeToRefs(projectsLoader)
const { getProjects } = projectsLoader
await getProjects()

//Grouped Collabs
const { getGroupedCollabs, groupedCollabs } = useCollabs()
await getGroupedCollabs(projects.value ?? [])

const columnsWithCollabs = columns(groupedCollabs)
</script>

<template>
  <DataTable v-if="projects" :columns="columnsWithCollabs" :data="projects" />
</template>

<style scoped></style>
