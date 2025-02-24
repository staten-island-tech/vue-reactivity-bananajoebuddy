<template>
  <div class = "container">
  <div><UsagiCom /></div>
  <div><ThingsView></ThingsView></div>
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
/* Container for each stat bar */
.stat-bar {
  width: 100%;
  max-width: 300px;
  height: 30px;
  background-color: #e0e0e0; /* Light gray background */
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

.USAGIDLE {
  width: 100%;
  height: 110%;
}

</style>

