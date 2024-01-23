<template>
  <v-app-bar class="header">
    <img class="header__icon" :src="BildIcon" alt="BILD Logo" />
    <div class="header__slider">
      <v-btn
        @click="handleClick(element)"
        variant="tonal"
        v-for="element in getTagByContent()"
      >
        {{ element }}
      </v-btn>
    </div>
  </v-app-bar>
</template>

<script setup lang="ts">
import BildIcon from "@/assets/bild.svg";
const emit = defineEmits(["updateTags"]);

const getTagByContent = () => [
  "Politik",
  "Sport",
  "Unterhaltung",
  "Regional",
  "Politik",
  "Sport",
  "Unterhaltung",
  "Regional",
  "Politik",
  "Sport",
  "Unterhaltung",
  "Regional",
];

const handleClick = (element: string) => {
  console.log("click");
  console.log(element);
};
</script>

<style lang="scss">
.header {
  &__icon {
    margin: 8px;
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
