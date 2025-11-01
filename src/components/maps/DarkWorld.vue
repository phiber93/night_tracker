<script setup lang="ts"></script>

<template>
  <div class="darkworld">
    <img src="/src/assets/darkworld.webp" />
  </div>
</template>

<style>
.darkworld {
  max-width: 512px;
  max-height: 512px;
  position: relative;
  aspect-ratio: 1/1;
  flex-shrink: 1;

  & img {
    height: 100%;
    width: 100%;
  }
}
</style>
