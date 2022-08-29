<template>
  <li
    mt-10px
  >
    {{ item.content }}
    <button btn @click="todoStore.removeItem(item)">
      remove
    </button>
  </li>
</template>

<script setup lang="ts">
  import { useTodoStore } from '~/stores'
  import type { Item } from '~/stores'

  defineProps<{
    item: Item
  }>()
  const todoStore = useTodoStore()
</script>
