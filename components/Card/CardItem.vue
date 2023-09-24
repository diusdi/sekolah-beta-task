<!-- eslint-disable vue/no-mutating-props -->
<template>
  <div
    :class="[
      'item-task d-flex align-items-start border-bottom pt-3 pb-4',
      isGrid ? 'col-12 col-md-6 col-lg-4' : 'col-12',
    ]"
  >
    <input
      id="task"
      v-model="task.isDone"
      type="checkbox"
      name="status"
      class="me-2 mt-2"
      :checked="task.isDone"
    />
    <div
      :class="[
        'd-flex flex-column',
        task.isDone ? 'text-decoration-line-through fst-italic' : '',
      ]"
    >
      <nuxt-link class="title-task mb-1" :to="'app/detail/' + task.id">{{
        task.title
      }}</nuxt-link>
      <div class="category-task small text-muted">
        {{ task.category }}
      </div>
      <div class="description-task small">
        {{ task.description }}
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    task: {
      type: Object,
      // eslint-disable-next-line vue/require-valid-default-prop
      default: 'Untitled',
    },
    isGrid: {
      type: Boolean,
      required: true,
      default: false,
    },
  },
}
</script>
