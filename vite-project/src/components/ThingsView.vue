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
  width: 10%; /* Adjusted from px to rem for scalability */
  height: max-content; /* Using rem instead of vh */
  background-color: #fcf4dd;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  overflow-y: auto;
}

.sidebar-item {
  display: flex;
  align-items: center;
  gap: 0.625rem; /* 10px converted to rem */
}

.sidebar-item-image {
  width: 5rem; /* Converted 80px to rem */
  height: 5rem;
  object-fit: contain;
  border-radius: 0.3125rem; /* 5px converted */
}

.feed-button {
  padding: 0.3125rem 0.625rem; /* 5px 10px converted */
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 0.3125rem;
  cursor: pointer;
  transition: background 0.3s;
}

.feed-button:hover {
  background-color: #388e3c;
}

/* Mobile responsiveness */
@media (max-width: 768px) {
  .sidebar {
    width: 100%; /* Full width on smaller screens */
    height: auto; /* Allow it to shrink */
  }
}
</style>

//use reactive if you need the data inside thing to react use react //use ref //use slot for button
in card, usually emit
