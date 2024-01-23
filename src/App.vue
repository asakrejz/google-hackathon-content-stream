<template>
  <v-app>
    <v-main>
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
      <div class="content">
        <a href="https://www.bild.de">
          <img src="https://via.placeholder.com/300x250" alt="Bild" />
          <div>
            <span>Kicker</span>
            <span>Headline</span>
          </div>
        </a>
      </div>
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
import BildIcon from "./assets/bild.svg";
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

.content {
  margin-top: 8px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
