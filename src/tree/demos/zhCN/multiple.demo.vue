<markdown>
# 多选节点

设置 `multiple` 来允许多选节点。
</markdown>

<script lang="ts" setup>
import type { TreeOption } from 'naive-ui'
import { repeat } from 'seemly'
import { ref } from 'vue'

function createData(level = 4, baseKey = ''): TreeOption[] | undefined {
  if (!level)
    return undefined
  return repeat(6 - level, undefined).map((_, index) => {
    const key = `${baseKey}${level}${index}`
    return {
      label: createLabel(level),
      key,
      children: createData(level - 1, key)
    }
  })
}

function createLabel(level: number): string {
  if (level === 4)
    return '道生一'
  if (level === 3)
    return '一生二'
  if (level === 2)
    return '二生三'
  if (level === 1)
    return '三生万物'
  return ''
}

const data = createData()
const value = ref([])
</script>

<template>
  <n-tree multiple block-line :data="data" />
  <n-divider />
  <n-tree v-model:selected-keys="value" multiple block-line :data="data" />
</template>
