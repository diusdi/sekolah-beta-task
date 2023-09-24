<template>
  <div class="py-4">
    <div class="container">
      <div
        class="title border-bottom d-flex align-items-center justify-content-between py-2"
      >
        <h5>Article</h5>
        <div class="d-flex align-items-center ms-auto">
          <div class="d-flex align-items-center justify-content-end w-100">
            <span class="mx-1">view as</span>
            <button
              class="btn btn-outline-secondary py-1 px-2"
              @click="isGrid = !isGrid"
            >
              {{ isGrid ? 'Grid' : 'List' }}
            </button>
          </div>
        </div>
      </div>
      <div class="list-article row">
        <ArticleItem
          v-for="(article, i) in articles"
          :key="i"
          :article="article"
          :is-grid="isGrid"
        />
      </div>
    </div>
  </div>
</template>
<script>
import ArticleItem from '@/components/Card/ArticleItem.vue'

export default {
  components: {
    ArticleItem,
  },
  layout: 'custom',
  data() {
    return {
      // Daftar Artikel
      articles: [
        {
          id: 1,
          title: 'Judul Artikel 1',
        },
        {
          id: 2,
          title: 'Judul Artikel 2',
        },
        {
          id: 3,
          title: 'Judul Artikel 3',
        },
      ],
      isGrid: false,
    }
  },
}
</script>
<style></style>
