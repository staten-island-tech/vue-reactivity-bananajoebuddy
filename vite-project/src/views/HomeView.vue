<template>
  <div class = "container">
  <div><ThingsView></ThingsView></div>
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
  justify-content: contain;
  align-items: flex-start;
  flex-direction: row;
  width: 100vw;  /* Full viewport width */
  height: 100vh;
}

.stat-bar {
  width: 100%; /* Full width */
  height: 30px; /* Fixed height */
  background-color: #ccc; /* Light gray background */
  border-radius: 15px; /* Rounded corners */
  position: relative;
}

.stat-background {
  width: 100%; /* Full width background */
  height: 100%; /* Full height background */
  background-color: #ddd; /* Light gray background for the bar */
  border-radius: 15px; /* Rounded corners */
}

.stat-fill {
  height: 100%; /* Full height of the bar */
  background-color: #4caf50; /* Green color for the fill */
  transition: width 1s; /* Smooth animation as the bar shrinks */
}

.stat-text {
  position: absolute; /* Position the text inside the bar */
  top: 0;
  left: 50%; /* Center the text */
  transform: translateX(-50%); /* Exactly center it */
  color: white; /* White color for the text */
  font-weight: bold; /* Make text bold */
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
  width: 25%;
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



@media (max-width: 768px) {
  .layout {
    flex-direction: row;
    align-content: space-evenly;
  }
}
</style>
