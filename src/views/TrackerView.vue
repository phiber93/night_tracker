<script setup lang="ts">
import WorldMap from '@/components/maps/WorldMap.vue';
import type { IItemLocation } from '@/lib/interfaces';

defineProps<{
  lightWorldLocations: IItemLocation[];
  darkWorldLocations: IItemLocation[];
  ligthWorldEntrances: IItemLocation[];
  darkWorldEntrances: IItemLocation[];
}>();
</script>

<template>
  <div class="map-wrapper">
    <WorldMap
      :item-locations="lightWorldLocations"
      :entrance-locations="ligthWorldEntrances"
      image-src="/src/assets/lightworld.webp"
    />
    <WorldMap
      :item-locations="darkWorldLocations"
      :entrance-locations="darkWorldEntrances"
      image-src="/src/assets/darkworld.webp"
    />
  </div>
</template>

<style>
.map-wrapper {
  display: flex;
  flex-direction: row;
}
</style>
