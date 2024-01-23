<template>
  <a class="article" href="https://www.bild.de">
    <img class="article__image" :src="imageUrl" alt="Bild" />
    <div>
      <span>{{ headline }}</span>
    </div>
  </a>
</template>

<script lang="ts">
export default {
  props: {
    url: {
      type: String,
      default:
        "https://www.bild.de/politik/inland/politik-inland/benzin-pasta-schnitzel-prost-teuerjahr-2024-86599812.bildMobile.html",
    },
    headline: {
      type: String,
      default: "Headline",
    },
  },
  data: () => ({
    imageUrl: "https://a.bildstatic.de/img/bild-logo.4ba8a06e.jpg",
  }),
  async mounted() {
    console.log(this.url);
    this.imageUrl = (await this.fetchImageUrl(this.url)) || this.imageUrl;
  },
  methods: {
    fetchImageUrl(url: string) {
      const test = `https://www.bild.de${url}`;
      console.log(test);
      return fetch(test)
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
