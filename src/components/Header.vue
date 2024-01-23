<template>
  <v-app-bar class="header">
    <img class="header__icon" src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e3/Logo_BILD.svg/1200px-Logo_BILD.svg.png" alt="BILD Logo" />
    <div class="header__slider">
      <v-btn
        @click="handleClick(element)"
        variant="tonal"
        v-for="element in data"
      >
        {{ element }}
      </v-btn>
    </div>
  </v-app-bar>
</template>

<script lang="ts">
import BildIcon from "@/assets/bild.svg?inline";

export default {
  components: {
    BildIcon,
  },
  props: {
    categories: {
      type: Array,
      default: () => [],
    },
  },
  data: () => ({
    data: [],
  }),
  mounted() {
    this.data = this.categories
  },
  updated() {
    this.data = this.categories
  },
  methods: {
    handleClick(category: string) {
      this.$emit("update-content", category);
    },
  },
}
</script>

<style lang="scss">
.header {
  &__icon {
    margin: 8px;
    width: 40px;
  }

  &__slider {
    margin-right: 8px;
    display: flex;
    gap: 8px;
    flex-direction: row;
    justify-content: start;
    width: 100%;
    overflow-x: auto;
    overflow-y: hidden;

    -ms-overflow-style: none;
    scrollbar-width: none;

    &::-webkit-scrollbar {
      display: none;
    }
  }
}
</style>
