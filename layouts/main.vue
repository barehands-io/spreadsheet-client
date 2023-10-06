<template>
  <div class="flex justify-center">
    <div class="flex gap-x-2">
      <NuxtLink :to="{ name: 'index' }">Home</NuxtLink>
      <NuxtLink :to="{ name: 'summary' }">Summary</NuxtLink>
    </div>
  </div>
  <slot></slot>

  <client-only>
    <DebugDock />
  </client-only>
</template>
<script setup lang="ts"></script>
