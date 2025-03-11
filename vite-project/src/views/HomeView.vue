<template>
  <div class="container">
    <div>
      <div class="sidebar">
        <div v-for="(thing, index) in things" :key="index" class="sidebar-item">
          <img :src="thing.src" alt="thing.image" class="sidebar-item-image" />
          <button @click="useItem(thing)">{{ thing.type }}</button>
        </div>
      </div>
    </div>
    <div><UsagiCom /></div>
    <div class="statbarcontainer">
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
    </div>
  </div>
</template>

<script setup>
import UsagiCom from '@/components/UsagiCom.vue'
import StatBars from '@/components/StatBars.vue'

import { defineProps, ref, onMounted, onUnmounted } from 'vue'

const things = [
  { src: '/cockroach.png', stats: 5, type: 'food' },
  { src: '/yakult.png', stats: 5, type: 'liquid' },
  { src: '/shower.png', stats: 30, type: 'clean' },
]

const props = defineProps({
  things: {
    type: Array,
    required: true,
  },
})

/* 
takes the type 

*/

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
.container {
  display: flex;
  justify-content: flex-start; /* Aligns elements from left to right */
  align-items: center; /* Aligns vertically */
  width: 100vw;
  height: 100vh;
}

.USAGIDLE {
  width: 100%;
  height: 110%;
}

.sidebar {
  flex: 1;
  max-width: 30vw; /* Shrinks with screen */
  min-width: 10vw;
  height: 100dvh;
  background-color: #fcf4dd;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-content: flex-start;
  align-items: center;
  padding-top: 25%;
  padding-bottom: 25%;
}

.sidebar-item {
  width: 60%;
  height: 60%;
  display: flex;
  align-items: center;
}

.sidebar-item-image {
  width: 100%; /* Converted 80px to rem */
  height: 50%;
  object-fit: contain;
  border-radius: 0.3125rem; /* 5px converted */
}
.statbarcontainer {
  flex-direction: column;
  display: flex;
}

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

<!-- store all the data here, the one from stat bars and things view 
 
  take the information from stat bar put it into a javascript file
  when button is clicked, you 

 when button is clicked 
  - if button type is this, do that function
  - function adds to "hungervalue" simultanously as stat decreases




-->
