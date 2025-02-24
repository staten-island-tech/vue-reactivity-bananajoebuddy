<template>
  <div class="sidebar-container">
    <div><ThingsView></ThingsView></div>
  </div>
  <div class = "container">
  <div><UsagiCom /></div>
  <div><StatBars></StatBars></div>
  </div>
</template>

<script setup>
import UsagiCom from '@/components/UsagiCom.vue'
import ThingsView from '@/components/ThingsView.vue'
import StatBars from '@/components/StatBars.vue'
</script>
<style scoped>
.container {
  display: flex;
  gap: 20px;
  align-items: flex-start;
}
.sidebar-container {
  display: flex;
}
@media (max-width: 768px) {
  .layout {
    flex-direction: column;
    align-items: center;
  }
}
</style>
