<script setup lang="ts">
const shopsanityModel = defineModel('shopsanity', { required: true });
const entranceModel = defineModel('entrance', { required: true });
</script>

<template>
  <div class="settings">
    <label>
      Shopsanity
      <input type="checkbox" v-model="shopsanityModel" />
    </label>
    <label>
      Entrance
      <input type="checkbox" v-model="entranceModel" />
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
