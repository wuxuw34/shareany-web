<template>
  <div class="flex flex-col gap-3 h-full">
    <div class="flex flex-row items-center justify-between">
      <span class="text-muted-foreground">公共剪切板</span>
      <div class="bg-primary/10 rounded-full px-2 text-primary">
        <span># 取件码: 123</span>
      </div>
    </div>
    <textarea
      class="w-full flex-1 h-full shadow resize-none rounded-md focus-visible:outline-2 outline-0 px-3 py-2 transition-all duration-100 bg-secondary/1"
      placeholder="输入任何想要分享的内容..."
      @change="handleChange"
    ></textarea>
  </div>
</template>

<script setup lang="ts">
export interface TextProps {
  value?: string;
  onChange?: (value: string) => void;
  type: "text";
}

const text = ref<string>("");

function handleChange(e: Event) {
  text.value = (e.target as HTMLTextAreaElement).value;
}
</script>

<style lang="scss" scoped></style>
