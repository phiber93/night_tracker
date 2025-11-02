<script setup lang="ts">
import type { IItemLocation } from '@/lib/interfaces';
import { ref } from 'vue';

defineProps<IItemLocation>();

const state = ref<'available' | 'checked'>('available');
</script>

<template>
  <button
    class="item-location"
    :class="state"
    :style="`top:${top}%; left:${left}%`"
    @click="state = 'checked'"
    @click.right.prevent="state = 'available'"
  >
    <span class="sr-only">{{ name }}</span>
  </button>
</template>

<style>
.item-location {
  position: absolute;
  width: 2.5%;
  height: 2.5%;
  border: 1px black solid;

  &.available {
    background-color: green;
  }

  &.checked {
    background-color: gray;
  }
}
</style>
