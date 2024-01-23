<template>
  <a class="article" href="https://www.bild.de">
    <img
      v-if="isPremium"
      class="article__premium"
      src="@/assets/bild-plus.svg"
      alt="Bild"
    />
    <img class="article__image" :src="imageUrl" alt="Bild" />
    <div class="article__category">{{ category }}</div>
    <div class="article__text">
      <span class="article__text--headline">{{ headline }}</span>
    </div>
  </a>
</template>

<script lang="ts">
export default {
  props: {
    isPremium: {
      type: Boolean,
      default: false,
    },
    url: {
      type: String,
      default:
        "https://www.bild.de/politik/inland/politik-inland/benzin-pasta-schnitzel-prost-teuerjahr-2024-86599812.bildMobile.html",
    },
    headline: {
      type: String,
      default: "Headline",
    },
    category: {
      type: String,
      default: null,
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
  position: relative;

  &__image {
    width: 100%;
  }

  &__premium {
    position: absolute;
    top: 8px;
    left: 0;
    z-index: 1;

    width: 60px;
    height: 32px;
  }

  &__category {
    padding: 5px;
    border: 2px;
    border-radius: 5px;
    background-color: gray;
    color: white;
    position: absolute;
    top: 10px;
    right: 10px;
  }

  &__text {
    background: linear-gradient(
      rgba(33 37 41 / 0%) 0%,
      rgba(33 37 41 / 70%) 100%
    );
    position: absolute;
    font-family: "Roboto", sans-serif;
    font-weight: 700;
    font-size: 24px;
    color: white;
    text-shadow: 0 2px 8px rgba(0 0 0 / 60%);
    bottom: 0;
    width: 100%;
    padding: 16px;
  }
}
</style>
