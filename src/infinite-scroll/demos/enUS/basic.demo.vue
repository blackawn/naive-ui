<markdown>
# Basic
</markdown>

<script lang="ts" setup>
import { ref } from 'vue'

const count = ref(6)
function handleLoad() {
  count.value += 1
}
</script>

<template>
  <n-infinite-scroll style="height: 240px" :distance="10" @load="handleLoad">
    <div v-for="i in count" :key="i" class="item">
      {{ i }}
    </div>
  </n-infinite-scroll>
</template>

<style>
.item {
  display: flex;
  align-items: center;
  height: 46px;
  justify-content: center;
  margin-bottom: 10px;
  background-color: rgba(0, 128, 0, 0.16);
}

.item:last-child {
  margin-bottom: 0;
}
</style>
