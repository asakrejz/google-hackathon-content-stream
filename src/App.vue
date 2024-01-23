<template>
  <v-app>
    <v-main>
      <Header :categories="categories" @update-content="updateContent"></Header>
      <Content :articles="currentArticles"></Content>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Header from "./components/Header.vue";
import Content from "./components/Content.vue";
import { testData } from "./components/data/test-data.js";

const getTagByContent = () => [
  "sports",
  "people_shows",
  "politics",
  "technology_science",
  "fashion_beauty_lifestyle",
  "cars_motors",
  "digital_life",
  "money_business",
  "travel",
];

export default {
  components: {
    Header,
    Content,
  },
  data: () => ({
    articles: testData,
    currentArticles: [],
    categories: getTagByContent(),
  }),
  async mounted() {
    this.currentArticles = this.articles.slice(1, 5).map((article: any) => ({
      url: article.url,
      headline: article.headline,
      category: article.upday_category,
      isPremium: article.is_premium,
    }));
  },
  methods: {
    updateContent(category: string) {
      this.currentArticles = this.articles
      .filter((article: any) => article.upday_category === category)
      .slice(1, 5).map((article: any) => ({
          url: article.url,
          headline: article.headline,
          category: article.upday_category,
          subCategory: article.upday_sub_category,
          isPremium: article.is_premium,

        }));

      this.categories = [ ...new Set(this.currentArticles.map((article: any) => article.subCategory))];
    }
  }
};
</script>
