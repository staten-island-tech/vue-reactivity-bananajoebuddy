<template>
  <div class="sidebar">
    <div v-for="(thing, index) in things" :key="index" class="sidebar-item">
      <img :src="thing.src" alt="thing.image" class="sidebar-item-image" />
      <button 
        class="feed-button"
        @click="feedThing(thing)"
      >
        Feed
      </button>
    </div>
  </div>
</template>

<script setup>
// Declare the things array
const things = [
  { src: '/cockroach.png', stats: 5, type: 'hunger' },
  { src: '/yakult.png', stats: 5, type: 'thirst' },
  { src: '/shower.png', stats: 10, type: 'hygiene' },
]

// Define the event to update the stat in the parent component
defineEmits(['updateStat'])

const feedThing = (thing) => {
  // Emit the event with the stat type and value
  emit('updateStat', { type: thing.type, value: thing.stats })
}
</script>

<style scoped>
/* Styles remain the same */
</style>
