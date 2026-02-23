<template>
  <MainContentText />
</template>

<script setup lang="ts">
import { type TextProps } from "./text.vue";

export type MainContentProps = TextProps;

const props = defineProps<MainContentProps>();
</script>
