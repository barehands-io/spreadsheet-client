<template>
  <!-- Loader when data is being fetched -->
  <div v-if="isLoading" class="text-center py-5">
    <div class="loader"></div>
    <p>Loading...</p>
  </div>

  <!-- Display data when fetched -->
  <div v-else-if="data?.data">
    <div class="bg-white p-4 rounded-md shadow-sm">
      <h2 class="text-xl font-bold mb-4">Organizations Location Summary</h2>
      <ul>
        <li v-for="location in data.data.data" :key="location._id" class="mb-2">
          <span class="font-bold">{{ location._id }}:</span>
          <span>{{ location.numberOfOrganizations }}</span>
        </li>
      </ul>
    </div>
  </div>

  <!-- Error message -->
  <div v-else class="bg-red-500 text-white p-4 rounded-md mb-6">
    {{ error }}
  </div>
  <!--  <Debug :data="{ data }" />-->
</template>

<script setup lang="ts">
import axios from "axios";

const data = ref<any>();

const isLoading = ref(false);

const error = ref("");

function getData() {
  isLoading.value = true;
  error.value = "";
  axios
    .get("http://localhost:3800/location")
    .then((res) => {
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
