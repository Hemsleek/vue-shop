<template>
    <div class="search-result flex-grow">
        <header class="bg-white pb-6">
            <nav class="flex items-center justify-between h-20 px-4">

                <img src="/vectors/back.svg" alt="<==" @click="searchActive = false" />
                <img src="/vectors/cart.svg" alt="cart" />

            </nav>

            <template>
                <div class="my-2 pl-5">
                    <p class="">Headphone</p>
                    <p class="text-2xl font-extrabold mt-2">TMA Wireless</p>
                </div>
                <div class="flex justify-between items-center pl-5 pr-2 mt-8 mb-4 w-11/12 text-lg">
                    <span
                    v-for="(option,optionIndex) in options" :key="`search-option${optionIndex}`"
                    :class="optionIndex===0 ? 'border rounded-md px-4 flex items-center py-1' : 'flex items-center'"
                    >
                         <img
                            v-show="option==='Filter'"
                            class="w-5 h-5 mr-4"
                            src="vectors/sliders.svg"
                         />

                        {{option}}

                         <img
                            v-show="option==='Newest'"
                            class="w-4 h-4 ml-2"
                            src="vectors/arrow-up.svg"
                         />
                    </span>
                </div>
            </template>

        </header>

  </div>
</template>

<script>
export default {
  name: 'SearchResult',
  component: {},
  data: () => ({
    options: 'Filter,Relevance,Newest,Price'.split(',')
  })
}
</script>

<style lang="scss" scoped>

</style>
