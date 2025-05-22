<template>

  <!-- This is a Input component for searching restaurants. -->
  <div class="input-group">
    <input
      v-model="keyword"
      @keyup.enter="submit"
      type="text"
      class="form-control"
      placeholder="ค้นหาร้านอาหาร เช่น บางแสน"
    />

    <button @click="submit" class="btn btn-primary">
      🔍 ค้นหา
    </button>
  </div>

</template>



<script setup lang="ts">

// Default Keyword in Search Input
import { ref } from 'vue'
const keyword = ref('บางซื่อ')

// define events emit
const emit = defineEmits(['onSearch'])

// define submit function to main component
const submit = () => {
  emit('onSearch', keyword.value)
}
</script>
