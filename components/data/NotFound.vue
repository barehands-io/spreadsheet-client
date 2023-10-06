<template>
  <div class="flex justify-center items-center">
    <div class="flex flex-col gap-y-8 items-center">
      <i :class="icon" class="text-8xl"></i>
      <p class="text-3xl">
        {{ message }}
      </p>
      <NuxtLink to="/" class="btn-primary btn">Go Home</NuxtLink>
    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps({
  message: {
    type: String,
    default: "Not Found",
  },
  icon: {
    type: String,
    default: "fa-thin fa-receipt",
  },
});
</script>

<style scoped></style>
