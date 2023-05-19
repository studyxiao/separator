<script setup lang="ts">
const router = useRouter()
</script>

<template>
  <div class="mx-auto max-w-7xl px-6 py-32 text-center sm:py-40 lg:px-8 ">
    <p class=" text-8xl font-medium leading-8 mb-8 lg:mb-16">
      404
    </p>
    <h1 class="mt-4 text-3xl font-light tracking-tight  sm:text-5xl">
      Page not found
    </h1>
    <div class="mt-10 flex justify-center">
      <button
        class="text-sm font-medium leading-7 bg-white/30 px-4 py-2 rounded-lg hover:bg-white/60 transition-colors"
        @click="router.back()"
      >
        <span aria-hidden="true">&larr;</span> Go Back
      </button>
    </div>
  </div>
</template>

<route lang="yaml">
meta:
  layout: 404
</route>
