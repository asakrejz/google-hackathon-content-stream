<template>
  <div class="content">
    <Article
      v-for="article in articles"
      :url="article.url"
      :headline="article.headline"
      :category="article.category"
      :is-premium="article.isPremium"
    ></Article>
  </div>
</template>

<script setup lang="ts">
import Article from "./Article.vue";
import { testData } from "./data/test-data.js";

const articles = testData.slice(1, 10).map((article: any) => ({
  url: article.url,
  headline: article.headline,
  category: article.upday_category,
  isPremium: article.is_premium,
}));
</script>

<style lang="scss">
.content {
  margin: 8px;
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  grid-gap: 8px;

  @media (min-width: 800px) {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>
