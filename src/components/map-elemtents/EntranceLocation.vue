<script setup lang="ts">
import type { IItemLocation } from '@/lib/interfaces';
import { ref } from 'vue';

defineProps<IItemLocation>();

const state = ref<'available' | 'checked'>('available');
</script>

<template>
  <button
    class="entrance-location"
    :class="state"
    :style="`top:${top}%; left:${left}%`"
    @click="state = 'checked'"
    @click.right.prevent="state = 'available'"
  >
    <span class="sr-only">{{ name }}</span>
  </button>
</template>

<style>
.entrance-location {
  position: absolute;
  width: 3%;
  height: 3%;
  border: 1px black solid;
  border-radius: 100%;

  &.available {
    background-color: green;
  }

  &.checked {
    background-color: gray;
  }
}
</style>
