<script setup>
import { onMounted, ref } from "vue";
import DataTable from "./components/DataTable.vue";

const items = ref([]);
onMounted( async () => {
  const response = await fetch('https://api.sampleapis.com/cartoons/cartoons2D');
  items.value = await response.json();
  
});
</script>

<template>
  <div class="p-8 bg-gray-100 min-h-screen">
    <DataTable :items="items" />
  </div>
</template>
