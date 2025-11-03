<script setup lang="ts">
import { EntraneShuffleOptions } from '@/lib/enums';

const shopsanityModel = defineModel('shopsanity', { required: true });
const entranceModel = defineModel<EntraneShuffleOptions>('entrance', { required: true });
</script>

<template>
  <div class="settings">
    <label>
      Shopsanity
      <input type="checkbox" v-model="shopsanityModel" />
    </label>
    <label>
      Entrance
      <select v-model="entranceModel">
        <option v-for="option in EntraneShuffleOptions" :key="option" :value="option">
          {{ option }}
        </option>
      </select>
    </label>
  </div>
</template>

<style>
label {
  display: flex;
  align-items: center;
}

.settings {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
</style>
