<template>
  <div id="app">
    <TheHeader />
    <main class="container">
      <Hero />
      <div class="row mb-2">
        <TheArticle
          v-for="(article, index) in articles"
          :key="index"
          :article="article"
        />
      </div>
    </main>
  </div>
</template>

<script>
import TheHeader from '@/components/TheHeader.vue'
import Hero from '@/components/TheHero.vue'
import TheArticle from '@/components/CardArticle.vue'
export default {
  components: {
    TheHeader,
    Hero,
    TheArticle,
  },

  data() {
    return {
      articles: [],
    }
  },
  async fetch() {
    await this.$axios
      .get('v1/cnn-news')
      .then((res) => (this.articles = res.data.data))
  },
  mounted() {
    console.log('Artikel: ', this.articles)
  },
}
</script>
<style></style>
