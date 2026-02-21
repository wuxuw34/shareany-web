<template>
  <div class="flex flex-row gap-2 bg-[rgba(255,255,255,0.9)] w-fit p-4 rounded-2xl">
    <div
      v-for="app in apps"
      :key="app.name"
      class="flex flex-col items-center gap-1"
    >
      <Icon
        :icon="app.icon"
        class="size-[64px] rounded-md"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { Icon } from "@iconify/vue";
import { DOCKER_APPS } from "~/constants/docker";

const apps = ref<DockerApp[]>(DOCKER_APPS);
</script>
