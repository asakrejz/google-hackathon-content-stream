<template>
  <div class="content">
    <Article></Article>
    <Article></Article>
    <Article></Article>
    <Article></Article>
    <Article></Article>
  </div>
</template>

<script setup lang="ts">
import Article from "./Article.vue";
</script>

<style lang="scss">
.content {
  margin: 8px;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 8px;
}
</style>
