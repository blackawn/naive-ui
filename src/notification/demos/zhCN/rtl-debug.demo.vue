<markdown>
# Rtl Debug
</markdown>

<script lang="ts" setup>
import {
  NAvatar,
  NButton,
  unstableNotificationRtl,
  useNotification
} from 'naive-ui'
import { h, ref } from 'vue'

const rtlEnabled = ref(true)
const rtlStyles = [unstableNotificationRtl]

function NotificationButton() {
  const notification = useNotification()

  return h(
    NButton,
    {
      onClick: () => {
        notification.create({
          title: 'Rtl Notification',
          content: 'No avatar and icon'
        })
        notification.info({
          title: 'Rtl Notification',
          content: 'Info icon'
        })
        notification.create({
          title: 'Rtl Notification',
          description: 'Whit avatar and description',
          content: `Wouldn't it be nice if we were older
Then we wouldn't have to wait so long
And wouldn't it be nice to live together
In the kind of world where we belong
You know its gonna make it that much better
When we can say goodnight and stay together
Wouldn't it be nice if we could wake up
In the morning when the day is new
And after having spent the day together
Hold each other close the whole night through`,
          meta: '2019-5-27 15:11',
          avatar: () =>
            h(NAvatar, {
              size: 'small',
              round: true,
              src: 'https://07akioni.oss-cn-beijing.aliyuncs.com/07akioni.jpeg'
            })
        })
        const n = notification.create({
          title: 'Rtl Notification + Button',
          content: `I cant get no satisfaction
I cant get no satisfaction
Cause I try and I try and I try and I try
I cant get no, I cant get no`,
          meta: '2019-5-27 15:11',
          action: () =>
            h(
              NButton,
              {
                text: true,
                type: 'primary',
                onClick: () => {
                  n.destroy()
                }
              },
              {
                default: () => 'close'
              }
            )
        })
      }
    },
    { default: () => 'Show some notification' }
  )
}
</script>

<template>
  <n-space><n-switch v-model:value="rtlEnabled" />Rtl</n-space>
  <n-space>
    <n-config-provider :rtl="rtlEnabled ? rtlStyles : undefined">
      <n-notification-provider>
        <NotificationButton />
      </n-notification-provider>
    </n-config-provider>
  </n-space>
</template>
