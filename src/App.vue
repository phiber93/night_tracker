<script setup lang="ts">
import { computed, ref } from 'vue';
import SettingsView from './views/SettingsView.vue';
import TrackerView from './views/TrackerView.vue';
import type { IItemLocation } from './lib/interfaces';
import { alwaysLocationsLightWorld } from './lib/locations/light-world/always-locations';
import { nonEntranceItemLocationsLightWorld } from './lib/locations/light-world/non-entrance-locations';
import { shopLocationsLightWorld } from './lib/locations/light-world/shop-locations';
import { alwaysLocationsDarkworld } from './lib/locations/dark-world/always-locations';
import { shopLocationsDarkWorld } from './lib/locations/dark-world/shop-locations';
import { nonEntranceItemLocationsDarkWorld } from './lib/locations/dark-world/non-entrance-locations';

const shopsanityModel = ref(true);
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

const darkWorldLocations = computed(() => {
  const allLocations: IItemLocation[] = [...alwaysLocationsDarkworld];

  if (entranceModel.value) {
    return allLocations;
  }

  for (const nonEntranceLocation of nonEntranceItemLocationsDarkWorld) {
    allLocations.push(nonEntranceLocation);
  }

  if (shopsanityModel.value) {
    for (const shopsanityLocation of shopLocationsDarkWorld) {
      allLocations.push(shopsanityLocation);
    }
  }
  return allLocations;
});
</script>

<template>
  <TrackerView
    :light-world-locations="lightWorldLocations"
    :dark-world-locations="darkWorldLocations"
  />
  <SettingsView v-model:shopsanity="shopsanityModel" v-model:entrance="entranceModel" />
</template>
