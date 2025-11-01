<script setup lang="ts">
import ItemLocation from '../map-elemtents/ItemLocation.vue'
import { alwaysLocationsLightWorld } from '@/lib/light-world-locations'
</script>

<template>
  <div class="lightworld">
    <img src="/src/assets/lightworld.webp" />
    <ItemLocation
      v-for="location in alwaysLocationsLightWorld"
      :key="location.name"
      :name="location.name"
      :top="location.top"
      :left="location.left"
    />
  </div>
</template>

<style>
.lightworld {
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
