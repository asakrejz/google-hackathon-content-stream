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

<script lang="ts">
import Article from "./Article.vue";

export default {
  components: {
    Article,
  },
  props: {
    articles: {
      type: Array,
      default: () => [],
    },
  },
};

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
