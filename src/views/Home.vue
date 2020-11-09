
<template>
  <div class="home flex-grow" :class="searchActive ? 'bg-white' : 'bg-gray-200'">
    <header class="bg-white pb-6">
      <nav class="flex items-center justify-between h-20 px-4">
        <template v-if="!searchActive">
          <img src="/vectors/menu.svg" alt="" />

          <div class="flex items-center">
            <img src="/vectors/logo.svg" class="mr-2 h-6" alt="Audio" />
            <img src="/vectors/Audio.svg" class="h-4" alt="Audio" />
          </div>

          <img src="/img/john.png" alt="John" />
        </template>
        <template v-else>
          <img src="/vectors/back.svg" alt="<==" @click="searchActive = false" />

          <span class="text-2xl font-medium">Search</span>

          <span />
        </template>
      </nav>

      <div class="px-4 mt-4">
        <template v-if="!searchActive">
          <p class="text-xl font-light text-gray-700">Hi, Andrea</p>

          <p class="text-4xl font-bold mb-3">What are you looking for today?</p>
        </template>

        <form
          @submit.prevent
          class="border rounded-lg border-gray-400 px-2 py-1 flex items-center"
        >
          <img src="/vectors/search.svg" alt="" class="mr-2" />
          <input
            type="text"
            v-model="searchQuery"
            class="py-2 flex-grow focus:outline-none text-lg"
            placeholder="Search product"
            @focus="searchActive = true"
          />
        </form>
      </div>
    </header>

    <main class="px-4" v-if="!searchActive">
      <div class="flex items-center justify-between pl-4 py-6">
        <span
          class="py-1 px-3 rounded-full cursor-pointer font-normal" v-for="(cat, catIndex) in categories"
          :key="`home-cat_${catIndex}`"
          v-text="cat"
          :class="{
            'bg-green-400 text-white' :  selectedCategory === catIndex,
            'text-gray-600': selectedCategory !== catIndex
          }"
        />
      </div>

      <div class="rounded-xl bg-white flex items-center p-4">
        <p class="flex flex-col">
          <span class="text-4xl font-semibold">TMA-2 <br> Modular Headphone</span>
          <span class="mt-3 text-green-600">Shop now</span>
        </p>
        <img src="/img/tma-2_modular.png" class="h-40 w-40 object-cover" alt="">
      </div>

      <div class="grid grid-cols-3 gap-x-3 my-6">
        <div
          class="bg-white shadow-xs rounded-lg flex flex-col p-3"
          v-for="(product, productIndex) in products"
          :key="`home-product_${productIndex}`"
        >
          <img :src="product.image" alt="TMA" />
          <span class="my-1" v-text="product.name" />
          <span class="font-semibold">USD {{ product.price }}</span>
        </div>
      </div>
    </main>

    <home-search v-else />
  </div>
</template>

<script>
import HomeSearch from '@/components/HomeSearch'
export default {
  name: 'Home',
  components: {
    HomeSearch
  },
  data: () => ({
    searchActive: false,
    searchQuery: '',
    categories: 'Headphones,Headbands,Earpods,Cable'.split(','),
    selectedCategory: 0,
    products: [
      { name: 'TMA-2 HD Wireless', price: 350, image: '/img/tma-2_modular.png' },
      { name: 'CO2 Cable', price: 25, image: '/img/co2_cable.png' },
      { name: 'CO2 Cable', price: 25, image: '/img/co2_cable.png' }
    ]
  })
}
</script>

<style lang="scss" scoped></style>
