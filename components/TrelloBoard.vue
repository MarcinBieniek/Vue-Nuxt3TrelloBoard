<script setup lang="ts">

  import type {Column} from "~/types";
  import {nanoid} from "nanoid";

  const columns = ref<Column[]>([
    {
      id: nanoid(),
      title: "Backlog",
      tasks: [
        {
          id: nanoid(),
          title: "Create margeing landing page",
          createdAt: new Date()
        },
        {
          id: nanoid(),
          title: "Develop cool new feature",
          createdAt: new Date()
        },
        {
          id: nanoid(),
          title: "Fix bug",
          createdAt: new Date()
        }
      ]
    },
    {
      title: "Selected for Dev",
      id: nanoid(),
      tasks: []
    },
    {
      title: "In progress",
      id: nanoid(),
      tasks: []
    },
    {
      title: "QA",
      id: nanoid(),
      tasks: []
    },
    {
      title: "Complete",
      id: nanoid(),
      tasks: []
    },
  ])

</script>

<template>
  <section>
    <div v-for="column in columns" :key="column.id">
      <header>
        {{ column.title }}
      </header>
      <p v-for="task in column.tasks" :key="task.id">
        {{ task.title }}
      </p>
    </div>
  </section>
</template>