<markdown>
# 最大标签数量

可以设定固定的数量，或者使用 `responsive` 设定响应式的最大标签数量。
</markdown>

<script lang="ts" setup>
import { ref } from 'vue'

const value = ref(null)
const options = [
  {
    label: 'Everybody\'s Got Something to Hide Except Me and My Monkey',
    value: 'song0',
    disabled: true
  },
  {
    label: 'Drive My Car',
    value: 'song1'
  },
  {
    label: 'Norwegian Wood',
    value: 'song2'
  },
  {
    label: 'You Won\'t See',
    value: 'song3',
    disabled: true
  },
  {
    label: 'Nowhere Man',
    value: 'song4'
  },
  {
    label: 'Think For Yourself',
    value: 'song5'
  },
  {
    label: 'The Word',
    value: 'song6'
  },
  {
    label: 'Michelle',
    value: 'song7',
    disabled: true
  },
  {
    label: 'What goes on',
    value: 'song8'
  },
  {
    label: 'Girl',
    value: 'song9'
  },
  {
    label: 'I\'m looking through you',
    value: 'song10'
  },
  {
    label: 'In My Life',
    value: 'song11'
  },
  {
    label: 'Wait',
    value: 'song12'
  }
]
</script>

<template>
  <n-space vertical>
    <n-select
      v-model:value="value"
      placeholder="maxTagCount = responsive"
      multiple
      :options="options"
      max-tag-count="responsive"
      size="small"
    />
    <n-select
      v-model:value="value"
      placeholder="maxTagCount = 3"
      multiple
      :options="options"
      :max-tag-count="3"
    />
  </n-space>
</template>
