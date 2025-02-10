<template>
  <div class="sidebar">
    <div v-for="(thing, index) in things" :key="index" class="sidebar-item">
      <img :src="thing.src" alt="thing.image" class="sidebar-item-image" />
      <span class="sidebar-item-stats">{{ thing.stats }}</span>
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
  position: fixed;
  top: 0;
  left: 0;
  width: 200px;
  height: 100vh;
  background-color: #333;
  padding: 20px;
  color: white;
  display: flex;
  flex-direction: column;
  gap: 20px;
  overflow-y: auto;
}

.sidebar-item {
  display: flex;
  align-items: center;
  gap: 10px;
}

.sidebar-item-image {
  width: 40px;
  height: 40px;
  object-fit: cover;
  border-radius: 5px;
}

.sidebar-item-stats {
  font-size: 18px;
}
</style>
