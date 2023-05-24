<script setup lang="ts">
const name = ref('')
const showName = computed(() => name.value?.length > 0 ? ` ${name.value} ` : '')
</script>

<template>
  <section class="mx-auto w-full lg:w-4/12 2xl:w-[600px] mt-20">
    <div class="relative transition-all hover:scale-110 hover:drop-shadow-xl">
      <div class="flex flex-col space-y-8 bg-[#2f2f2f] rounded-2xl p-10 text-[#fefefe] text-2xl cursor-pointer outline-dashed outline-4 outline-offset-transparent outline-offset-2 outline-yellow-300 hover:outline-offset-4 min-w-[200px] lg:min-w-[30rem] text-center">
        <span class="text-3xl text-yellow-500 animate-bounce">Drag me!</span>
        <span class="truncate">——————{{ showName }}——————</span>
      </div>
      <a href="" class="absolute inset-0"><span class="hidden">
        ——————{{ showName }}——————
      </span></a>
    </div>

    <!-- divider -->
    <div class="relative mt-20 mb-4">
      <div class="absolute inset-0 flex items-center" aria-hidden="true">
        <div class="w-full border-t border-gray-200" />
      </div>
      <div class="relative flex justify-center">
        <span class="bg-[#212121] px-2 text-sm text-gray-300">Edit</span>
      </div>
    </div>
    <!-- divider end -->

    <div class="flex flex-col items-start bg-[#2f2f2f] rounded-2xl p-10 text-[#fefefe] transition-all text-2xl">
      <div class="flex w-full items-center">
        <span class="text-gray-100 mr:2 lg:mr-4">Category</span>
        <input
          v-model="name"
          placeholder="Optional"
          type="text"
          class="rounded-lg flex-1 border w-full border-yellow-200 px-4 py-2 focus:outline-none focus:ring-2 focus:ring-yellow-500 focus:border-transparent placeholder-gray-600 bg-black/30 transition-all"
        >
      </div>
    </div>
  </section>
</template>

<route lang="yaml">
meta:
  layout: home
</route>
