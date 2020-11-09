<template>
  <main class="px-4">
    <p class="px-1 mb-3">Latest search</p>

    <div
      class="flex-items-center px-1 py-3 flex items-center"
      v-for="(val, valIndex) in latestSearch"
      :key="`latest-search_${valIndex}`"
    >
      <img src="/vectors/time.svg" alt="time" class="mr-4">
      <span class="flex-grow" v-text="val" />
      <img src="/vectors/close.svg" alt="close">
    </div>

    <p class="px-1 mb-3 mt-8">Popular Products</p>

    <div class="flex items-center my-2 py-1" v-for="i in 5" :key="i">
      <img src="/img/tma-2_modular.png" alt="" class="mr-3 bg-gray-100 rounded-lg h-20" />
      <div class="flex flex-col">
        <span class="text-lg mb-1">TMA-2 Comfort Wireless </span>
        <span class="font-medium">USD 270</span>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  data: () => ({
    latestSearch: 'TMA2 Wireless,Cable'.split(',')
  })
}
</script>
