<script setup lang="ts">

  import type {Column} from "@/types";
  import {nanoid} from "nanoid";
  import draggable from "vuedraggable";

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
  <section >

    <draggable
      v-model="columns"
      group="columns"
      item-key="id"
      class="flex gap-4 overflow-x-auto items-start"
      :animation="150"
      handle=".drag-handle"
    >
    <template #item="{element: column}: {element: Column }">
      <div
        class="column bg-gray-200 p-5 rounded min-w-[250px]"
      >
        <header class="font-bold mb-2">
          <DragHandle />
          {{ column.title }}
        </header>
        <TrelloBoardTask v-for="task in column.tasks" :task="task" />
        <footer>
          <button class="text-gray-500">+ Add a Card</button>
        </footer>
      </div>
    </template>
    </draggable>

  </section>
</template>