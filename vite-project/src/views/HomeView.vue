<template>
  <div class = "container">
  <div><UsagiCom /></div>
  <ThingsView @updateStat="handleUpdateStat" />
    <StatBars :hungerStat="hungerStat" :thirstStat="thirstStat" :hygieneStat="hygieneStat" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import UsagiCom from '@/components/UsagiCom.vue'
import ThingsView from '@/components/ThingsView.vue'
import StatBars from '@/components/StatBars.vue'

const handleUpdateStat = (stat) => {
  if (stat.type === 'hunger') {
    hungerStat.value = Math.min(hungerStat.value + stat.value, 100)
  } else if (stat.type === 'thirst') {
    thirstStat.value = Math.min(thirstStat.value + stat.value, 100)
  } else if (stat.type === 'hygiene') {
    hygieneStat.value = Math.min(hygieneStat.value + stat.value, 100)
  }
}
</script>
<style scoped>
.container {
  display: flex;
  justify-content: contain;
  align-items: flex-start;
  justify-content: contain;
  align-items: flex-start;
  flex-direction: row;
  width: 100vw;  /* Full viewport width */
  height: 100vh;
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


}


.sidebar-item {
 width: 10rem;
 height: 30%;
 display: flex;
 align-items: center;
}


.sidebar-item-image {
 width: 100%; /* Converted 80px to rem */
 height: 50%;
 object-fit: contain;
 border-radius: 0.3125rem; /* 5px converted */
}

.stat-bar {
  width: 100%; /* Full width of the container */
  max-width: 500px; /* Optional: To prevent it from becoming too wide */
  height: 30px; /* Fixed height */
  background-color: #ccc; /* Light gray background */
  border-radius: 15px; /* Rounded corners */
  position: relative;
  margin-bottom: 1rem; /* Optional: Spacing between the bars */
  box-sizing: border-box; /* Prevents overflow */
}

.stat-background {
  width: 100%; /* Full width background */
  height: 100%; /* Full height background */
  background-color: #ddd; /* Light gray background for the bar */
  border-radius: 15px; /* Rounded corners */
  overflow: hidden; /* Ensures that the fill doesn’t overflow */
}

.stat-fill {
  height: 100%; /* Full height of the bar */
  background-color: #4caf50; /* Green color for the fill */
  transition: width 1s ease-out; /* Smooth animation as the bar fills/shrinks */
}

.stat-text {
  position: absolute; /* Position the text inside the bar */
  top: 50%; /* Center the text vertically */
  left: 50%; /* Center the text horizontally */
  transform: translate(-50%, -50%); /* Exactly center it */
  color: white; /* White color for the text */
  font-weight: bold; /* Make text bold */
  font-size: 1rem; /* Optional: Adjust text size */
  z-index: 1; /* Ensure the text is always on top */
}




</style>

