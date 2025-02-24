<template>
  <div class="sidebar">
    <div v-for="(thing, index) in things" :key="index" class="sidebar-item">
      <img :src="thing.src" alt="thing.image" class="sidebar-item-image" />
      <button class="feed-button"></button>
    </div>
  </div>
</template>

<script setup>
const things = [
  {
    src: '/cockroach.png',
    stats: 5,
  },
  {
    src: '/yakult.png',
    stats: 5,
  },
  {
    src: '/shower.png',
    stats: 30,
  },
]
</script>

<style scoped>
.sidebar {
  width: 50vh; /* Adjusted from px to rem for scalability */
  height: 50%; 
  background-color: #fcf4dd;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  align-content: space-evenly;
  align-content: contain;

}

.sidebar-item {
  display: flex;
  align-items: center;
  gap: 0.625rem; /* 10px converted to rem */
}

.sidebar-item-image {
  width: 50%; /* Converted 80px to rem */
  height: 50vh;
  object-fit: contain;
  border-radius: 0.3125rem; /* 5px converted */
}


/* Mobile responsiveness */

</style>

