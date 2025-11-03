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
import { EntraneShuffleOptions } from './lib/enums';
import { dungeonsSimpleEntrancesLightWorld } from './lib/entrances/light-world/dungeons-simple-entrances';
import { dungeonsSimpleEntrancesDarkWorld } from './lib/entrances/dark-world/dungeons-simple-entrances';

const shopsanityModel = ref(true);
const entranceModel = ref<EntraneShuffleOptions>(EntraneShuffleOptions.DUNGEONS_SIMPLE);

const lightWorldLocations = computed(() => {
  const allLocations: IItemLocation[] = [...alwaysLocationsLightWorld];

  if (entranceModel.value === EntraneShuffleOptions.CROSSED) {
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

  if (entranceModel.value === EntraneShuffleOptions.CROSSED) {
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

const lightWorldEntrances = computed(() => {
  switch (entranceModel.value) {
    case EntraneShuffleOptions.NONE:
      return [];
    case EntraneShuffleOptions.DUNGEONS_SIMPLE:
      return [...dungeonsSimpleEntrancesLightWorld];
    case EntraneShuffleOptions.DUNGEONS_FULL:
      return [...dungeonsSimpleEntrancesLightWorld];
    case EntraneShuffleOptions.CROSSED:
      return [...dungeonsSimpleEntrancesLightWorld];
    default:
      return [];
  }
});

const darkWorldEntrances = computed(() => {
  switch (entranceModel.value) {
    case EntraneShuffleOptions.NONE:
      return [];
    case EntraneShuffleOptions.DUNGEONS_SIMPLE:
      return [...dungeonsSimpleEntrancesDarkWorld];
    case EntraneShuffleOptions.DUNGEONS_FULL:
      return [...dungeonsSimpleEntrancesDarkWorld];
    case EntraneShuffleOptions.CROSSED:
      return [...dungeonsSimpleEntrancesDarkWorld];
    default:
      return [];
  }
});
</script>

<template>
  <TrackerView
    :light-world-locations="lightWorldLocations"
    :dark-world-locations="darkWorldLocations"
    :ligth-world-entrances="lightWorldEntrances"
    :dark-world-entrances="darkWorldEntrances"
  />
  <SettingsView v-model:shopsanity="shopsanityModel" v-model:entrance="entranceModel" />
</template>
