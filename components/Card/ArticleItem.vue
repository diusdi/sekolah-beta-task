<!-- eslint-disable vue/no-mutating-props -->
<template>
  <div
    :class="[
      'item-article d-flex align-items-start border-bottom pt-3 pb-4',
      isGrid ? 'col-12 col-md-6 col-lg-4' : 'col-12',
    ]"
  >
    <nuxt-link
      class="title-article mb-1"
      :to="'article/detail/' + article.id"
      >{{ article.title }}</nuxt-link
    >
  </div>
</template>
<script>
export default {
  props: {
    article: {
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
