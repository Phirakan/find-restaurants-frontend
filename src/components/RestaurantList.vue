<template>
  <!-- list content -->
  <div class="space-y-4">
    <div v-if="restaurants.length === 0" class="text-center py-8">
      <div class="text-5xl mb-4">🍽️</div>
      <p class="text-gray-500">ยังไม่มีร้านอาหารที่แสดง กรุณาค้นหา</p>
    </div>
    
    <!-- loop restaurants list -->
    <div 
      v-for="(item, index) in restaurants" 
      :key="index"
      class="bg-amber-50 rounded-lg p-4 hover:shadow-md transition-shadow border border-amber-100"
    >
      <div class="flex items-start gap-3">
        <div class="flex-grow">
          <h3 class="font-medium text-lg text-amber-900">{{ item.name }}</h3>
          <p class="text-amber-700 text-sm mt-1">
            <span class="inline-flex items-center">
              <span class="mr-1">📍</span> {{ item.vicinity || 'ไม่ระบุที่อยู่' }}
            </span>
          </p>
          
          <!-- rating -->
          <div class="mt-2 flex flex-wrap gap-2">
            <span v-if="item.rating" class="px-2 py-0.5 bg-amber-200 text-amber-800 rounded text-xs flex items-center">
              ⭐ {{ item.rating || '0.0' }}
            </span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
// Type of data
interface Restaurant {
  name: string;
  vicinity: string;
  key: string;
  rating?: number;
}

defineProps({
  restaurants: {
    type: Array as () => Restaurant[],
    required: true
  }
})
</script>