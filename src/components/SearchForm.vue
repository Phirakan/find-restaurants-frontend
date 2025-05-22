<template>

  <!-- input form -->
  <div class="relative">
    <div class="flex flex-col sm:flex-row gap-2">
      <div class="relative flex-grow">
        <input
          v-model="keyword"
          @keyup.enter="submit"
          type="text"
          class="w-full px-4 py-3 pl-10 rounded-lg border border-amber-200 focus:border-amber-400 focus:ring-2 focus:ring-amber-300 focus:outline-none transition"
          placeholder="ค้นหาร้านอาหาร เช่น บางแสน"
        />

        <!-- submit button -->
         <button 
        @click="submit" 
        class="px-6 py-3 bg-amber-500 hover:bg-gray text-black font-medium rounded-lg transition-colors shadow-sm"
      >
       🔍
        ค้นหา
      </button>
      </div>
     
    </div>

      <!-- popular search button -->
    <div class="mt-2 flex flex-wrap gap-2">
      <button 
        v-for="(suggestion, index) in suggestions" 
        :key="index"
        @click="searchSuggestion(suggestion)"
        class="px-3 py-1 text-sm bg-amber-100 text-amber-800 rounded-full hover:bg-amber-200 transition-colors" >
        {{ suggestion }}
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">

import { ref } from 'vue'

// Default Keyword in Search Input
const keyword = ref('บางซื่อ')

// Popular search suggestions
const suggestions = ref(['บางแสน', 'สยาม', 'เยาวราช', 'ทองหล่อ', 'อโศก'])

// define events emit
const emit = defineEmits(['onSearch'])

// define submit function to main component
const submit = () => {
  if (keyword.value.trim()) {
    emit('onSearch', keyword.value)
  }
}

// Search using suggestion
const searchSuggestion = (suggestion: string) => {
  keyword.value = suggestion
  submit()
}
</script>