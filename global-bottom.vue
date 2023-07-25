<script setup>
import HeartRate from './components/HeartRate.vue';
</script>

<template>
  <div
    v-show="$slidev.nav.currentPage >= 18 && $slidev.nav.currentLayout!== 'end'"
    class="fixed top-6 right-6 z-50"
  >
    <heart-rate />
  </div>
</template>