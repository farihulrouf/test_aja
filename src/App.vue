<script setup>
import CandidatePlatforms from "./components/backgroundChecking.vue";
</script>

<template>
  <div class="container">
    <h1 class="title">Test API Candidate Platforms</h1>
    <CandidatePlatforms />
  </div>
</template>

<style scoped>
.container {
  max-width: 600px;
  margin: 20px auto;
  text-align: center;
}

.title {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 20px;
}
</style>
