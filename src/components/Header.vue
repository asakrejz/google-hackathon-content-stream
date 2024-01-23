<template>
  <v-app-bar class="header">
    <img class="header__icon" :src="BildIcon" alt="BILD Logo" />
    <div class="header__slider">
      <v-btn variant="tonal"> Politik </v-btn>
      <v-btn variant="tonal"> Sport </v-btn>
      <v-btn variant="tonal"> Unterhaltung </v-btn>
      <v-btn variant="tonal"> Regional </v-btn>
      <v-btn variant="tonal"> Politik </v-btn>
      <v-btn variant="tonal"> Sport </v-btn>
      <v-btn variant="tonal"> Unterhaltung </v-btn>
      <v-btn variant="tonal"> Regional </v-btn>
      <v-btn variant="tonal"> Politik </v-btn>
      <v-btn variant="tonal"> Sport </v-btn>
      <v-btn variant="tonal"> Unterhaltung </v-btn>
      <v-btn variant="tonal"> Regional </v-btn>
    </div>
  </v-app-bar>
</template>

<script setup lang="ts">
import BildIcon from "@/assets/bild.svg";
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
