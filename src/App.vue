<template>
  <!-- main content -->
  <div class="min-h-screen bg-gradient-to-b from-amber-50 to-orange-50">
    <div class="container mx-auto ">
      <header class=" text-center">
        <h1 class="text-3xl font-bold text-amber-800 mb-2">🍜 ค้นหาร้านอาหาร</h1>
        <p class="text-amber-600">ค้นหาร้านอาหารที่ดีที่สุดในพื้นที่ของคุณ</p>
      </header>
      
      <div class="max-w-2xl mx-auto mb-8">
        <SearchForm @onSearch="handleSearch" />
      </div>
      
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
        <div class="bg-white rounded-xl shadow-md p-4 overflow-hidden">
          <h2 class="text-xl font-semibold text-amber-800 mb-4 flex items-center">
            <span class="mr-2">📋</span> รายการร้านอาหาร
          </h2>
          <RestaurantList :restaurants="restaurants" />
        </div>
       
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">

//import components
import { ref } from 'vue'
import SearchForm from './components/SearchForm.vue'
import RestaurantList from './components/RestaurantList.vue'

const restaurants = ref([])

//function to handle search
const handleSearch = async (keyword: string) => {
  try {
    const response = await fetch(`http://127.0.0.1:8000/api/restaurants?keyword=${keyword}`)
    const data = await response.json()
    restaurants.value = data.results
  } catch (error) {
    console.error('Error fetching restaurants:', error)
  }
}
</script>