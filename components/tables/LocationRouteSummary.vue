<template>
  <div v-if="isLoading" class="text-center py-5">
    <div class="loader"></div>
    <p>Loading...</p>
  </div>

  <div v-else-if="data">
    <div
      class="min-w-full bg-white overflow-hidden shadow rounded-lg h-[500px] overflow-y-auto"
    >
      <table class="min-w-full leading-normal">
        <thead>
          <tr>
            <th
              class="px-5 py-3 border-b-2 border-gray-200 bg-gray-100 text-left text-xs font-semibold text-gray-600 uppercase tracking-wider"
            >
              Route
            </th>
            <th
              class="px-5 py-3 border-b-2 border-gray-200 bg-gray-100 text-left text-xs font-semibold text-gray-600 uppercase tracking-wider"
            >
              Location
            </th>
            <th
              class="px-5 py-3 border-b-2 border-gray-200 bg-gray-100 text-left text-xs font-semibold text-gray-600 uppercase tracking-wider"
            >
              Count
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in data.data.data">
            <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
              {{ item.route }}
            </td>
            <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
              {{ item.location }}
            </td>
            <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
              {{ item.count }}
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>

  <!-- Error message -->
  <div v-else class="bg-red-500 text-white p-4 rounded-md mb-6">
    {{ error }}
  </div>
</template>

<script setup lang="ts">
import axios from "axios";

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
    .get("http://localhost:3800/routes_locations")
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

<style scoped></style>
