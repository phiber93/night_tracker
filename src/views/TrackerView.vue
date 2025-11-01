<script setup lang="ts">
import DarkWorld from '@/components/maps/DarkWorld.vue'
import LightWorld from '@/components/maps/LightWorld.vue'
</script>

<template>
  <div class="map-wrapper"><LightWorld /> <DarkWorld /></div>
</template>

<style>
.map-wrapper {
  display: flex;
  flex-direction: row;
}
</style>
