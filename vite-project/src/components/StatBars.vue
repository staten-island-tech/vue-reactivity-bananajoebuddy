<template>
  <div>
    <p>Hunger:</p>
    <div class="stat-bar">
      <div class="stat-background">
        <div class="stat-fill" :style="{ width: hungerStat + '%' }"></div>
      </div>
      <div class="stat-text">{{ hungerStat }}%</div>
    </div>

    <p>Thirst:</p>
    <div class="stat-bar">
      <div class="stat-background">
        <div class="stat-fill" :style="{ width: thirstStat + '%' }"></div>
      </div>
      <div class="stat-text">{{ thirstStat }}%</div>
    </div>

    <p>Hygiene:</p>
    <div class="stat-bar">
      <div class="stat-background">
        <div class="stat-fill" :style="{ width: hygieneStat + '%' }"></div>
      </div>
      <div class="stat-text">{{ hygieneStat }}%</div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const hungerStat = ref(100)
const thirstStat = ref(100)
const hygieneStat = ref(100)

let intervalId = null

// Decrease stats every second
onMounted(() => {
  intervalId = setInterval(() => {
    if (hungerStat.value > 0) hungerStat.value -= 5
    if (thirstStat.value > 0) thirstStat.value -= 5
    if (hygieneStat.value > 0) hygieneStat.value -= 5
    if (hungerStat.value <= 0 && thirstStat.value <= 0 && hygieneStat.value <= 0) {
      clearInterval(intervalId)
    }
  }, 1000)
})

onUnmounted(() => {
  if (intervalId) {
    clearInterval(intervalId)
  }
})

// Method to increase stats
const increaseStat = (statType, value) => {
  if (statType === 'hunger') {
    hungerStat.value = Math.min(hungerStat.value + value, 100) // Don't exceed 100
  } else if (statType === 'thirst') {
    thirstStat.value = Math.min(thirstStat.value + value, 100) // Don't exceed 100
  } else if (statType === 'hygiene') {
    hygieneStat.value = Math.min(hygieneStat.value + value, 100) // Don't exceed 100
  }
}
</script>

<style scoped>
/* Styles remain the same */
</style>
