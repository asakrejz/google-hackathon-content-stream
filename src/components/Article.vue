<template>
  <a class="article" href="https://www.bild.de">
    <img class="article__image" :src="imageUrl" alt="Bild" />
    <div>
      <span>Kicker</span>
      <span>Headline</span>
    </div>
  </a>
</template>

<script lang="ts">
import { tSThisType } from "@babel/types";

export default {
  props: {
    url: {
      type: String,
      default: "https://www.bild.de",
    },
  },
  data: () => ({
    imageUrl: "https://a.bildstatic.de/img/bild-logo.4ba8a06e.jpg",
  }),
  async mounted() {
    this.imageUrl = (await this.fetchImageUrl(this.url)) || this.imageUrl;
  },
  methods: {
    fetchImageUrl(url: string) {
      return fetch(url)
        .then((response) => response.text())
        .then((html) => {
          // Parse the HTML to find the OG image URL
          const parser = new DOMParser();
          const doc = parser.parseFromString(html, "text/html");
          const ogImageElement = doc.querySelector('meta[property="og:image"]');
          const ogImageUrl = ogImageElement
            ? ogImageElement.getAttribute("content")
            : null;

          return ogImageUrl;
        });
    },
  },
};
</script>

<style lang="scss">
.article {
  &__image {
    width: 100%;
  }
}
</style>
