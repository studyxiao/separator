<script setup lang="ts">
import { Popover, PopoverButton, PopoverPanel } from '@headlessui/vue'

const { modelValue: currentEmoji } = defineModels<{
  modelValue: string
}>()
</script>

<template>
  <div>
    <Popover v-slot="{ open }" class="relative">
      <PopoverButton
        :class="open ? '' : 'text-opacity-90'"
        class="aspect-square p-1 rounded-full  transition-all flex justify-center items-center mt-[-16px] "
      >
        <span class="text-4xl">{{ currentEmoji }}</span>
      </PopoverButton>

      <transition
        enter-active-class="transition ease-out duration-100"
        enter-from-class="transform opacity-0 scale-95"
        enter-to-class="transform opacity-100 scale-100"
        leave-active-class="transition ease-in duration-75"
        leave-from-class="transform opacity-100 scale-100"
        leave-to-class="transform opacity-0 scale-95"
      >
        <PopoverPanel
          class="absolute left-1/2 z-10 -translate-x-1/2 transform px-4"
        >
          <Emoji v-model="currentEmoji" />
        </PopoverPanel>
      </transition>
    </Popover>
  </div>
</template>
