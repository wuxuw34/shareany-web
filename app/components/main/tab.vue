<template>
  <div class="relative w-fit">
    <div
      class="absolute left-0 top-[50%] translate-y-[-50%] w-0 flex items-center justify-center h-10 bg-white transition-[left] z-10 rounded-lg"
      ref="underlineRef"
    ></div>
    <div
      class="flex flex-row bg-primary/10 rounded-md px-2"
      ref="containerRef"
    >
      <button
        v-for="app in FUNC_APPS"
        :key="app.name"
        :id="app.name"
        :class="`py-4 flex px-6 flex-row items-center justify-center gap-1  text-muted-foreground hover:text-black cursor-pointer text-sm select-none z-20 ${
          active === app.name ? 'text-primary!' : ''
        }`"
        @click="handleClick(app.name)"
      >
        <Icon
          :icon="app.icon"
          class="w-4 h-5"
        />
        {{ app.name }}
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { Icon } from "@iconify/vue";
import { FUNC_APPS } from "~/constants/func";

const emits = defineEmits<{
  (e: "update", name: string): boolean;
}>();

const active = ref<string>(FUNC_APPS[0]!.name);
const containerRef = ref<HTMLDivElement | null>(null);
const underlineRef = ref<HTMLDivElement | null>(null);

onMounted(() => {
  updateUnderline(active.value);
  window.addEventListener("resize", handleResize);
});

onUnmounted(() => {
  window.removeEventListener("resize", handleResize);
});

function handleResize() {
  updateUnderline(active.value);
}

function handleClick(name: string) {
  if (active.value !== name) {
    active.value = name;
    updateUnderline(name);
    emits("update", name);
  }
}

function updateUnderline(name: string) {
  // 获取到所有子元素
  const items = containerRef.value?.children;
  if (!items?.length) return;
  const item = Array.from(items).find((el) => el.id === name);
  if (!item) return;
  // 获取到元素的位置
  const rect = item.getBoundingClientRect();
  // 更新元素
  underlineRef.value!.style.left = `${rect.left}px`;
  underlineRef.value!.style.width = `${rect.width}px`;
}
</script>
