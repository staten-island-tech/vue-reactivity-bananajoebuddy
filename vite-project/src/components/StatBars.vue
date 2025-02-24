<template>
  <div>
    <p>Hunger:</p>
  </div>
  <div class="stat-bar">
    <!-- The bar that fills based on the stat value -->
    <div class="stat-background">
      <div class="stat-fill" :style="{ width: stat + '%' }"></div>
    </div>
    <!-- Show the stat value inside the bar -->
    <div class="stat-text">{{ stat }}%</div>
  </div>
  <div>
    <p>Thirst:</p>
  </div>
  <div class="stat-bar">
    <!-- The bar that fills based on the stat value -->
    <div class="stat-background">
      <div class="stat-fill" :style="{ width: stat + '%' }"></div>
    </div>
    <!-- Show the stat value inside the bar -->
    <div class="stat-text">{{ stat }}%</div>
  </div>
  <div>
    <p>Hygiene:</p>
  </div>
  <div class="stat-bar">
    <!-- The bar that fills based on the stat value -->
    <div class="stat-background">
      <div class="stat-fill" :style="{ width: stat + '%' }"></div>
    </div>
    <!-- Show the stat value inside the bar -->
    <div class="stat-text">{{ stat }}%</div>
  </div>
</template>

<script setup>
// Import Vue's "ref" for reactive data
import { ref, onMounted, onUnmounted } from 'vue'

// Step 1: Create a ref for the stat value. We'll start at 100%.
const stat = ref(100)

// Step 2: Decrease the stat every second
let intervalId = null

// When the component is mounted (added to the page), we start decreasing the stat.
onMounted(() => {
  intervalId = setInterval(() => {
    // If the stat is above 0, decrease it by 5 each second
    if (stat.value > 0) {
      stat.value -= 5
    } else {
      clearInterval(intervalId) // Stop when the stat reaches 0
    }
  }, 100) // Update every second (1000ms)
})

// Clean up (stop the timer) when the component is removed from the page
onUnmounted(() => {
  if (intervalId) {
    clearInterval(intervalId)
  }
})
</script>

<style scoped>
/* Step 3: Style the stat bar */

</style>
