<markdown>
# A bit complex example
</markdown>

<script lang="ts" setup>
import { computed, ref } from 'vue'

const loading = ref(false)

const avatars = [
  'https://07akioni.oss-cn-beijing.aliyuncs.com/07akioni.jpeg',
  'https://avatars.githubusercontent.com/u/20943608?s=60&v=4',
  'https://avatars.githubusercontent.com/u/46394163?s=60&v=4',
  'https://avatars.githubusercontent.com/u/39197136?s=60&v=4',
  'https://avatars.githubusercontent.com/u/19239641?s=60&v=4'
]

const messages = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']

function mock(i: number) {
  return {
    key: `${i}`,
    value: i,
    avatar: avatars[i % avatars.length],
    message: messages[Math.floor(Math.random() * messages.length)]
  }
}

const items = ref(Array.from({ length: 10 }, (_, i) => mock(i)))
const noMore = computed(() => items.value.length > 16)

async function handleLoad() {
  if (loading.value || noMore.value)
    return
  loading.value = true
  await new Promise(resolve => setTimeout(resolve, 1000))
  items.value.push(...[mock(items.value.length), mock(items.value.length + 1)])
  loading.value = false
}
</script>

<template>
  <n-infinite-scroll style="height: 240px" :distance="10" @load="handleLoad">
    <div
      v-for="(item, index) in items"
      :key="item.key"
      class="message"
      :class="{ reverse: index % 5 === 0 }"
    >
      <img class="avatar" :src="item.avatar" alt="">
      <span> {{ item.message }} {{ index % 5 === 0 ? '?' : '' }}</span>
    </div>
    <div v-if="loading" class="text">
      Loading...
    </div>
    <div v-if="noMore" class="text">
      No More 🤪
    </div>
  </n-infinite-scroll>
</template>

<style>
.message {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
  padding: 10px;
}

.message:last-child {
  margin-bottom: 0;
}

.reverse {
  flex-direction: row-reverse;
}

.text {
  text-align: center;
}

.reverse .avatar {
  margin-left: 10px;
}

.avatar {
  width: 28px;
  height: 28px;
  border-radius: 50%;
  margin-right: 10px;
}
</style>
