<template>
  <div>
    <div>总共有: {{ itemCount }} 条数据。 - itemCount</div>
    <div>总共有: {{ todoStore.itemCount }} 条数据。 - todoStore.itemCount</div>
    <div>
      <input
        v-model="todoStore.newItem"
        type="text"
        mr-10px
        border
        class="border-[#ff6700]"
      >
      <button btn @click="addItem">
        add
      </button>
    </div>
    <ul>
      <TodoItem
        v-for="item of todoStore.items"
        :key="item.id"
        :item="item"
      />
    </ul>
  </div>
</template>

<script lang="ts" setup>
  import { storeToRefs } from 'pinia'
  import TodoItem from './todoItem.vue'
  import { useTodoStore } from '~/stores'

  const todoStore = useTodoStore()

  const { itemCount } = storeToRefs(todoStore)

  const addItem = async () => {
    const res = await todoStore.addItem()
    console.log(res, 'res')
  }
</script>
