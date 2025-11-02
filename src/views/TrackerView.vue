<script setup lang="ts">
import WorldMap from '@/components/maps/WorldMap.vue';
import type { IItemLocation } from '@/lib/interfaces';

defineProps<{
  lightWorldLocations: IItemLocation[];
  darkWorldLocations: IItemLocation[];
}>();
</script>

<template>
  <div class="map-wrapper">
    <WorldMap :locations="lightWorldLocations" image-src="/src/assets/lightworld.webp" />
    <WorldMap :locations="darkWorldLocations" image-src="/src/assets/darkworld.webp" />
  </div>
</template>

<style>
.map-wrapper {
  display: flex;
  flex-direction: row;
}
</style>
