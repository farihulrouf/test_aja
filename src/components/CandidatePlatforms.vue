<script setup>
import { ref, onMounted } from "vue";
import axios from "axios";

const platforms = ref([]);
const loading = ref(true);
const error = ref(null);

const fetchPlatforms = async () => {
  try {
    const response = await axios.get(
      "https://9093-103-19-78-162.ngrok-free.app/api/v1/candidate-platforms/1",
      {
        headers: {
          Authorization: "Bearer 37|eVBo4DanJRcOC7gbt7EqU1CBUgnWhe8HVW4wuaaNb853429c",
        },
      }
    );

    if (response.data.status) {
      platforms.value = response.data.data;
    } else {
      error.value = "Gagal mengambil data";
    }
  } catch (err) {
    error.value = "Terjadi kesalahan saat mengambil data";
  } finally {
    loading.value = false;
  }
};

onMounted(fetchPlatforms);
</script>

<template>
  <div class="container">
    <h2>Daftar Platform Kandidat</h2>
    <div v-if="loading">Memuat data...</div>
    <div v-else-if="error" class="error">{{ error }}</div>
    <ul v-else>
      <li v-for="platform in platforms" :key="platform.id">
        <strong>{{ platform.platform }}:</strong>
        <a :href="platform.url" target="_blank">{{ platform.url }}</a>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.container {
  max-width: 600px;
  margin: 20px auto;
  padding: 20px;
  text-align: center;
}

.error {
  color: red;
  font-weight: bold;
}
</style>
