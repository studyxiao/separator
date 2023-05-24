<script setup lang="ts">
import { Switch } from '@headlessui/vue'

defineOptions({
  name: 'IndexPage',
})
// 允许使用图标
const enabled = ref(false)
// 当前图标
const currentEmoji = ref('👨‍🚀')
const tmpEmoji = ref('')
// 分类名称
const name = ref('')
// 在收藏栏显示的标题
const bookmarkName = computed(() => {
  if (name.value.trim() === '')
    return '────────────'
  else
    return `────── ${name.value} ──────`
})

watch(enabled, (val) => {
  if (val) {
    currentEmoji.value = tmpEmoji.value
  }
  else {
    tmpEmoji.value = currentEmoji.value
    currentEmoji.value = ''
    handleHead()
  }
}, { immediate: true })

/**
 * 操作 head
 */
function handleHead() {
  useHead({
    title: bookmarkName.value,
    meta: [
      {
        name: 'description',
        content: 'Opinionated Vite Starter Template from vitesse',
      },
    ],
    link: [
      {
        rel: 'icon',
        type: 'image/svg+xml',
        href: () => `data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text x=%22-.1em%22 y=%22.9em%22 font-size=%2290%22>${currentEmoji.value}</text></svg>`,
      },
    ],
  })
}
handleHead()
</script>

<template>
  <div class="flex min-h-screen flex-col">
    <div class="relative bg-white p-4 lg:p-10 rounded-xl drop-shadow-xl mt-10 lg:min-w-[450px]">
      <div class="group relative cursor-pointer">
        <a class="absolute inset-0 z-10" :href="String(parseInt(Math.random() * 1000))">
          <span class=" text-transparent">
            {{ bookmarkName }}
          </span>
        </a>
        <div class="absolute -inset-0.5 rounded-xl bg-gradient-to-tr  from-pink-600 to-purple-600 opacity-50 blur transition duration-500 group-hover:opacity-100 group-hover:duration-300" />
        <span class="relative flex flex-col items-center rounded-xl bg-white px-7 py-8 space-y-4 leading-none ">
          <h3 class="text-lg font-medium text-pink-600 animate-bounce">Drag me to Bookmark</h3>
          <span>
            <span>
              {{ currentEmoji }}
            </span>
            <span>
              {{ bookmarkName }}
            </span>
          </span>
        </span>
      </div>
      <!-- divider -->
      <div class="relative mt-10 mb-4">
        <div class="absolute inset-0 flex items-center" aria-hidden="true">
          <div class="w-full border-t border-gray-300" />
        </div>
        <div class="relative flex justify-center">
          <span class="bg-white px-2 text-sm text-gray-500">Edit</span>
        </div>
      </div>
      <!-- divider end -->
      <div class="flex flex-col items-start justify-start">
        <div class="mb-4 flex w-full items-center">
          <span class="text-gray-700 mr:2 lg:mr-4">Category</span>
          <input
            v-model="name"
            placeholder="Optional"
            type="text"
            class="rounded-lg flex-1 border w-full border-gray-200 px-4 py-2 focus:outline-none focus:ring-2 focus:ring-pink-600 focus:border-transparent placeholder-slate-300"
          >
        </div>

        <div class="flex items-center justify-center min-h-[64px]">
          <span class="text-gray-700 mr:2 lg:mr-4">With Icon</span>
          <Switch v-model="enabled" class="relative inline-flex h-6 w-11 flex-shrink-0 cursor-pointer rounded-full border-2 border-transparent transition-colors duration-200 ease-in-out focus:outline-none focus:ring-2 focus:ring-pink-600 focus:ring-offset-2" :class="[enabled ? 'bg-pink-600' : 'bg-gray-200']">
            <span class="sr-only">Use setting</span>
            <span aria-hidden="true" class="pointer-events-none inline-block h-5 w-5 transform rounded-full bg-white shadow ring-0 transition duration-200 ease-in-out" :class="[enabled ? 'translate-x-5' : 'translate-x-0']" />
          </Switch>
          <EmojiSelector v-show="enabled" v-model="currentEmoji" />
        </div>
      </div>
    </div>
  </div>
</template>
