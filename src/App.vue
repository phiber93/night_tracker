<script setup lang="ts">
import { computed, ref } from 'vue';
import SettingsView from './views/SettingsView.vue';
import TrackerView from './views/TrackerView.vue';
import type { IItemLocation } from './lib/interfaces';
import { alwaysLocationsLightWorld } from './lib/locations/light-world/always-locations';
import { nonEntranceItemLocationsLightWorld } from './lib/locations/light-world/non-entrance-locations';
import { shopLocationsLightWorld } from './lib/locations/light-world/shop-locations';

const shopsanityModel = ref(false);
const entranceModel = ref(false);

const lightWorldLocations = computed(() => {
  const allLocations: IItemLocation[] = [...alwaysLocationsLightWorld];

  if (entranceModel.value) {
    return allLocations;
  }

  for (const nonEntranceLocation of nonEntranceItemLocationsLightWorld) {
    allLocations.push(nonEntranceLocation);
  }

  if (shopsanityModel.value) {
    for (const shopsanityLocation of shopLocationsLightWorld) {
      allLocations.push(shopsanityLocation);
    }
  }

  return allLocations;
});
</script>

<template>
  <TrackerView :light-world-locations="lightWorldLocations" />
  <SettingsView v-model:shopsanity="shopsanityModel" v-model:entrance="entranceModel" />
</template>

<style scoped></style>
