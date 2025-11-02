<script setup lang="ts">
import type { IItemLocation } from '@/lib/interfaces';
import ItemLocation from '../map-elemtents/ItemLocation.vue';

defineProps<{
  locations: IItemLocation[];
  imageSrc: string;
}>();
</script>

<template>
  <div class="map">
    <img :src="imageSrc" />
    <ItemLocation
      v-for="location in locations"
      :key="location.name"
      :name="location.name"
      :top="location.top"
      :left="location.left"
    />
  </div>
</template>

<style>
.map {
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
