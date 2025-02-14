<template>
  <div class="sidebar">
    <div v-for="(thing, index) in things" :key="index" class="sidebar-item">
      <img :src="thing.src" alt="thing.image" class="sidebar-item-image" />
      <button></button>
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
  width: 300px;
  height: max-content;
  background-color: #fcf4dd;
  padding: 10px;
  color: white;
  display: flex;
  flex-direction: column;
  gap: 170px;
  overflow-y: auto;
}

.sidebar-item {
  display: flex;
  align-items: center;
  gap: 10px;
}

.sidebar-item-image {
  width: 200px;
  height: 200px;
  object-fit: contain;
  border-radius: 5px;
}
</style>

//use reactive if you need the data inside thing to react use react //use ref //use slot for button
in card, usually emit
