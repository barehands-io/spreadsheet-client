<template>
  <div class="p-6 bg-gray-100">
    <h1 class="text-3xl font-bold">Summary</h1>

    <!-- Loader when data is being fetched -->
    <div v-if="isLoading" class="text-center py-5">
      <div class="loader"></div>
      <p>Loading...</p>
    </div>

    <!-- Error message -->
    <div v-if="error" class="bg-red-500 text-white p-4 rounded-md mb-6">
      {{ error }}
    </div>

    <!-- Display data when fetched -->
    <div v-else-if="data">
      <div class="grid grid-cols-2 gap-4 mb-6">
        <div class="bg-white p-4 rounded-md shadow-sm">
          <p class="font-bold">Total Companies:</p>
          <p>{{ data.summary.total_companies }}</p>
        </div>
        <div class="bg-white p-4 rounded-md shadow-sm">
          <p class="font-bold">Total Routes:</p>
          <p>{{ data.summary.total_routes }}</p>
        </div>
        <div class="bg-white p-4 rounded-md shadow-sm">
          <p class="font-bold">Skilled Workers:</p>
          <p>{{ data.summary.skilled_worker }}</p>
        </div>
        <div class="bg-white p-4 rounded-md shadow-sm">
          <p class="font-bold">Total Locations:</p>
          <p>{{ data.summary.total_locations }}</p>
        </div>
      </div>
    </div>
  </div>

  <LocationSummary />
</template>

<script setup lang="ts">
import axios from "axios";
import LocationSummary from "~/components/LocationSummary.vue";

definePageMeta({
  layout: "main",
  name: "summary",
});

const data = ref<any>();

const isLoading = ref(false);

const error = ref("");

function getData() {
  isLoading.value = true;
  error.value = "";
  axios
    .get("http://localhost:3800/summary")
    .then((res) => {
      console.log(res);
      data.value = res.data;
      isLoading.value = false;
    })
    .catch((err) => {
      error.value = err;
      isLoading.value = false;
    });
}

onMounted(() => {
  getData();
});
</script>

<style scoped>
.loader {
  border: 4px solid rgba(255, 255, 255, 0.3);
  border-radius: 50%;
  border-top: 4px solid #000;
  width: 40px;
  height: 40px;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
