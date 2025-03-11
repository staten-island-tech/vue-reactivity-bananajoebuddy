<template>
  <div>
    <p>Hunger:</p>
  </div>
  <div class="stat-bar">
    <!-- The bar that fills based on the stat value -->
    <div class="stat-background">
      <div class="stat-fill" :style="{ width: hungerstat + '%' }"></div>
    </div>
    <!-- Show the stat value inside the bar -->
    <div class="stat-text">{{ hungerstat }}%</div>
  </div>
  <div>
    <p>Thirst:</p>
  </div>
  <div class="stat-bar">
    <!-- The bar that fills based on the stat value -->
    <div class="stat-background">
      <div class="stat-fill" :style="{ width: thirststat + '%' }"></div>
    </div>
    <!-- Show the stat value inside the bar -->
    <div class="stat-text">{{ thirststat }}%</div>
  </div>
  <div>
    <p>Hygiene:</p>
  </div>
  <div class="stat-bar">
    <!-- The bar that fills based on the stat value -->
    <div class="stat-background">
      <div class="stat-fill" :style="{ width: hygienestat + '%' }"></div>
    </div>
    <!-- Show the stat value inside the bar -->
    <div class="stat-text">{{ hygienestat }}%</div>
  </div>
</template>

<script setup>
// Import Vue's "ref" for reactive data
import { ref, onMounted, onUnmounted } from 'vue'

const hungerstat = ref(100)
const thirststat = ref(100)
const hygienestat = ref(100)
// Step 2: Decrease the stat every second
let hungerInterval = null
let thirstInterval = null
let hygieneInterval = null
// When the component is mounted (added to the page), we start decreasing the stat.

const decreaseHunger = () => {
  if (hungerstat.value > 0) {
    hungerstat.value -= 5
  } else {
    clearInterval(hungerInterval)
  }
}

const decreaseThirst = () => {
  if (thirststat.value > 0) {
    thirststat.value -= 5
  } else {
    clearInterval(thirstInterval)
  }
}

const decreaseHygiene = () => {
  if (hygienestat.value > 0) {
    hygienestat.value -= 5
  } else {
    clearInterval(hygieneInterval)
  }
}

onMounted(() => {
  hungerInterval = setInterval(decreaseHunger, 1000)
  thirstInterval = setInterval(decreaseThirst, 1000)
  hygieneInterval = setInterval(decreaseHygiene, 1000)
})
// Clean up (stop the timer) when the component is removed from the page
onUnmounted(() => {
  clearInterval(hungerInterval)
  clearInterval(thirstInterval)
  clearInterval(hygieneInterval)
})
</script>
<style scoped>
/* Step 3: Style the stat bar */
.stat-bar {
  width: 100%;
  max-width: 300px;
  height: 30px;
  background-color: #2e2828; /* Light gray background */
  border-radius: 15px;
  overflow: hidden;
  position: relative;
  margin-bottom: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}
/* The colored part of the bar that decreases */
.stat-fill {
  height: 100%;
  width: 100%; /* Starts full */
  background: linear-gradient(90deg, #ff6363, #ffab40); /* Gradient effect */
  transition: width 0.3s ease-in-out; /* Smooth decrease */
}
/* Text displaying the percentage */
.stat-text {
  position: absolute;
  width: 100%;
  text-align: center;
  font-weight: bold;
  font-size: 14px;
  color: white;
  top: 50%;
  transform: translateY(-50%);
}
</style>
