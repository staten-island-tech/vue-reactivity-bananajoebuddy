<template>
  <div class="container">
    <!-- Minimal change: Add event listener to update stat -->
    <div><ThingsView @update-stat="updateStat" /></div>
    <div><UsagiCom /></div>
    <!-- Minimal change: Pass stat values as props to StatBars -->
    <div><StatBars :hungerStat="hungerStat" :thirstStat="thirstStat" :hygieneStat="hygieneStat" /></div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import ThingsView from '@/components/ThingsView.vue'
import UsagiCom from '@/components/UsagiCom.vue'
import StatBars from '@/components/StatBars.vue'

// Initial stat values (hunger, thirst, hygiene)
const hungerStat = ref(100)
const thirstStat = ref(100)
const hygieneStat = ref(100)

// Minimal change: Handle stat updates
const updateStat = ({ type, stat }) => {
  if (type === 'food') {
    hungerStat.value = Math.min(hungerStat.value + stat, 100)
  } else if (type === 'thirst') {
    thirstStat.value = Math.min(thirstStat.value + stat, 100)
  } else if (type === 'hygiene') {
    hygieneStat.value = Math.min(hygieneStat.value + stat, 100)
  }
}
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
 
 
 </style>
 
 
 
 
 