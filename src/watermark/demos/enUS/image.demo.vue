<markdown>
# Image

Put image here.

Please note about cross origin setting of the image URL. It will influence whether the image can be displayed.
</markdown>

<script lang="ts" setup>
import { ref } from 'vue'

const show = ref(false)
</script>

<template>
  <n-watermark
    v-if="show"
    image="https://07akioni.oss-cn-beijing.aliyuncs.com/07akioni.jpeg"
    cross
    fullscreen
    :font-size="16"
    :line-height="16"
    :width="384"
    :height="384"
    :x-offset="12"
    :y-offset="0"
    :image-width="64"
    :image-opacity="0.24"
  />
  <n-switch v-model:value="show" />
</template>
