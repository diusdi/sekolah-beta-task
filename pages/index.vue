<template>
  <div class="py-4">
    <div class="container">
      <div
        class="title border-bottom d-flex align-items-center justify-content-between py-2"
      >
        <h5>Task</h5>
        <div class="d-flex align-items-center ms-auto">
          <select
            v-model="searchQuery"
            class="form-select"
            aria-label="Default select example"
          >
            <option value="">Pilih Kategori</option>
            <option value="1">Kategori 1</option>
            <option value="2">Kategori 2</option>
            <option value="3">Kategori 3</option>
          </select>
          <div class="d-flex align-center justify-content-end w-100">
            <span class="me-2">View As</span>
            <button
              class="btn btn-outline-secondary py-1 px-3"
              @click="isGrid = !isGrid"
            >
              {{ isGrid ? 'Grid' : 'List' }}
            </button>
          </div>
        </div>
      </div>

      <div class="list-task row">
        <CardItem
          v-for="(task, i) in resultQuery"
          :key="i"
          :task="task"
          :is-grid="isGrid"
        />
      </div>
    </div>
  </div>
</template>
<script>
import CardItem from '@/components/Card/CardItem.vue'

export default {
  components: {
    CardItem,
  },
  layout: 'custom',
  data() {
    return {
      // Daftar task
      tasks: [
        {
          title: 'Task 1',
          description: 'ini deskripi',
          category: 'Kategori 1',
          isDone: false,
        },
        {
          title: 'Task 2',
          description: 'ini deskripi 2',
          category: 'Kategori 2',
          isDone: false,
        },
        {
          title: 'Task 3',
          description: 'ini deskripi 3',
          category: 'Kategori 3',
          isDone: false,
        },
      ],
      searchQuery: '',
      isCreating: false,
      isGrid: false,
    }
  },
  computed: {
    resultQuery() {
      if (this.searchQuery) {
        return this.tasks.filter((item) => {
          return this.searchQuery
            .toLowerCase()
            .split(' ')
            .every((v) => item.category.toLowerCase().includes(v))
        })
      } else {
        return this.tasks
      }
    },
  },
}
</script>
<style></style>
