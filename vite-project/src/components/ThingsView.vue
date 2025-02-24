 <template>
  <div class="sidebar">
    <div v-for="(thing, index) in things" :key="index" class="sidebar-item">
      <img :src="thing.src" alt="thing.image" class="sidebar-item-image" />
      <button ></button>
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
 
 
 
 
 
 
 </style>