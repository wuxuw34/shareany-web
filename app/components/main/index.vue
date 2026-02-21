<template>
  <div class="shadow rounded-md overflow-hidden">
    <MainTab @update="handleTabSelect" />
    <div class="h-[300px]">
      <MainContent />
    </div>
  </div>
</template>

<script setup lang="ts">
function handleTabSelect(name: string) {
  console.log("选择", name);
}
</script>
