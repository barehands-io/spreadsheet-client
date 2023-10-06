<template>
  <div class="bg-white p-6">
    <div class="flex justify-between">
      <p class="font-bold text-lg mb-4">All Routes:</p>
      <p class="font-bold text-lg mb-4">{{ total }}</p>
    </div>
    <p class="text-xs">Number of companies for reach route</p>

    <div class="rounded-md shadow-sm overflow-y-auto h-80">
      <ul>
        <li v-for="(item, index) in data" :key="index" class="mb-2">
          <div class="flex justify-between items-center gap-x-10">
            <div class="font-medium text-sm">{{ item.label }}:</div>
            <div class="text-base font-bold">
              {{ item.count }}
            </div>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  data: {
    type: Object,
    required: true,
  },
  total: {
    type: Number,
    required: true,
    default: 0,
  },
});
</script>
