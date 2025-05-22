<template>
  <div class="container py-4">
    <h1 class="text-center mb-4">🍜 ค้นหาร้านอาหาร</h1>
    <SearchForm @onSearch="handleSearch" />
    <div class="row mt-4">
      <div class="col-md-6">
        <RestaurantList :restaurants="restaurants" />
      </div>
      <div class="col-md-6">
        <MapView :locations="restaurants" />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import SearchForm from './components/SearchForm.vue'
import MapView from './components/MapView.vue'
import RestaurantList from './components/RestaurantList.vue'

const restaurants = ref([])

const handleSearch = async (keyword: string) => {
  const response = await fetch(`http://127.0.0.1:8000/api/restaurants?keyword=${keyword}`)
  const data = await response.json()
  restaurants.value = data.results
}
</script>
