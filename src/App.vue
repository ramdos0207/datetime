<script setup lang="ts">
import { ref } from 'vue';
import buttonsList from './components/buttonsList.vue';
const now = new Date();
const year = now.getFullYear();
const month = now.getMonth();
const date = now.getDate();
const selectedyear = ref<number>(year);
const selectedmonth = ref<number>(month+1);
const selecteddate = ref<number>(date);
</script>

<template>
  <buttonsList :begin="year-2" :end="year+2" :current="year" @update="(n) => selectedyear = n" />
  <buttonsList :begin="1" :end="12" :current="month+1" @update="(n) => selectedmonth = n" />
  <buttonsList :begin="1" :end="31" :current="date" @update="(n) => selecteddate = n" />
  {{ selectedyear }}-{{ selectedmonth }}-{{ selecteddate }}
</template>

<style scoped>
</style>
