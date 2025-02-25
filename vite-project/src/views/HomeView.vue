
<template>
  <div class = "container">
  <div><ThingsView></ThingsView></div>
  <div><UsagiCom /></div>
  <div><StatBars></StatBars></div>
  </div>
 </template>
 
 
 <script setup>
 import ThingsView from '@/components/ThingsView.vue'
 import UsagiCom from '@/components/UsagiCom.vue'
 import StatBars from '@/components/StatBars.vue'
 
 
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
 
 
 
 
 