<script setup lang="ts">
import { onMounted, ref } from 'vue'
import data from '@emoji-mart/data'
import { Picker } from 'emoji-mart'

const { modelValue: currentEmoji } = defineModels<{
  modelValue: string
}>()
const pickerRef = ref(null)

interface EmojiNode {
  id: string
  native: string
}

function handleEmojiSelect(emoji: EmojiNode) {
  currentEmoji.value = emoji.native
}

onMounted(() => {
  if (pickerRef.value != null) {
    const picker = new Picker({
      data,
      parent: pickerRef.value,
      searchPosition: 'sticky',
      skinTonePosition: 'search',
      previewPosition: 'none',
      autoFocus: true,
      onEmojiSelect: handleEmojiSelect,
    })
    // eslint-disable-next-line no-unused-expressions
    picker
  }
})
</script>

<template>
  <div ref="pickerRef" class=" inline-block backdrop-blur-lg" />
</template>
