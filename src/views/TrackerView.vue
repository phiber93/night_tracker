<script setup lang="ts">
import DarkWorld from '@/components/maps/DarkWorld.vue';
import LightWorld from '@/components/maps/LightWorld.vue';
import type { IItemLocation } from '@/lib/interfaces';

defineProps<{
  lightWorldLocations: IItemLocation[];
}>();
</script>

<template>
  <div class="map-wrapper"><LightWorld :locations="lightWorldLocations" /> <DarkWorld /></div>
</template>

<style>
.map-wrapper {
  display: flex;
  flex-direction: row;
}
</style>
