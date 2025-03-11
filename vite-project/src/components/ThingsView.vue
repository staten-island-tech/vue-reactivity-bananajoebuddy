<template>
  <div class="sidebar">
    <div v-for="(thing, index) in things" :key="index" class="sidebar-item">
      <img :src="thing.src" alt="thing.image" class="sidebar-item-image" />
      <button @click="useItem(thing)">{{ thing.type }}</button>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue'
const things = [
  { src: '/cockroach.png', stats: 5, type: 'food' },
  { src: '/yakult.png', stats: 5, type: 'water' },
  { src: '/shower.png', stats: 30, type: 'clean' },
]

const props = defineProps({
  things: {
    type: Array,
    required: true,
  },
})
</script>

<style scoped>
.sidebar {
  flex: 1;
  max-width: 30vw; /* Shrinks with screen */
  min-width: 10vw;
  height: 100dvh;
  background-color: #fcf4dd;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-content: flex-start;
  align-items: center;
  padding-top: 25%;
  padding-bottom: 25%;
}

.sidebar-item {
  width: 60%;
  height: 60%;
  display: flex;
  align-items: center;
}

.sidebar-item-image {
  width: 100%; /* Converted 80px to rem */
  height: 50%;
  object-fit: contain;
  border-radius: 0.3125rem; /* 5px converted */
}
</style>
