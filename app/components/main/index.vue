<template>
  <div class="shadow rounded-md overflow-hidden">
    <MainTab @update="handleTabSelect" />
    <div class="h-[300px] mt-3 shadow-[0px_4px_16px_rgba(0,0,0,0.1)] p-3">
      <MainContent type="text" />
    </div>
  </div>
</template>

<script setup lang="ts">
function handleTabSelect(name: string) {
  console.log("选择", name);
}
</script>
