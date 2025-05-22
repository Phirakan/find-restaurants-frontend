<template>

  <!-- This is a Restaurant List component. -->
  <div class="list-group">
    <!-- Loop all list of restaurants prop 'restaurants' -->
    <div
      v-for="(item, index) in restaurants"
      :key="index"
      class="list-group-item"
    >
    <!-- display restaurant -->
      <h5 class="mb-1">{{ item.name }}</h5>
  
    </div>
  </div>
</template>

<script setup lang="ts">

// Type of data
interface Restaurant {
  name: string;
  vicinity: string;
  key: string;
}


defineProps({
  restaurants: {
    type: Array as () => Restaurant[],
    required: true
  }
})
</script>
