<template>
  <div  id="map" style="width: 800px; height: 400px;"></div>
</template>

<script setup lang="ts">
import { onMounted } from 'vue'

const loadGoogleMapsScript = () => {
  return new Promise((resolve, reject) => {
    if (typeof google !== 'undefined') return resolve()

    const script = document.createElement('script')
    script.src =
      'https://maps.googleapis.com/maps/api/js?key=api_key&libraries=places'
    script.async = true
    script.defer = true
    script.onload = resolve
    script.onerror = reject
    document.head.appendChild(script)
  })
}

const initMap = () => {
  return new google.maps.Map(document.getElementById('map'), {
    center: { lat: 13.7563, lng: 100.5018 },
    zoom: 12,
  })
}

onMounted(async () => {
  await loadGoogleMapsScript()
  initMap()
})
</script>
