<template>
    <div class="search-result flex-grow">
        <header :class="{
            'result-clicked-bg pb-6':resultClicked===true,
            'bg-white pb-6':resultClicked===false
        }">
            <nav class="flex items-center justify-between h-20 px-4">

                <img src="/vectors/back.svg" alt="<==" @click=" resultClicked===true? resultClicked=!resultClicked : null" />

                <img v-if="showCart" src="/vectors/cart.svg" alt="cart" @click="showCart=true"/>

                <template v-else>
                    <span class="font-bold text-lg" v-text="`Shopping Cart`" />
                    <span />
                </template>
            </nav>
            <template v-if="showCart">
                <template v-if="!resultClicked">
                    <div class="my-1 pl-5">
                        <p class="">Headphone</p>
                        <p class="text-2xl font-extrabold mt-2">TMA Wireless</p>
                    </div>
                    <div class="flex justify-between items-center pl-5 pr-5 mt-8 mb-2 w-11/12 text-lg">
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

                <template v-else>

                    <div class="my-1 pl-5">
                        <p class="font-bold">USD 350</p>
                        <p class="text-4xl font-extrabold mt-2">TMA-2 <br /> HD WIRELESS</p>
                    </div>

                </template>
            </template>

        </header>
        <template v-if="showCart">
            <main class="result px-10 pt-6 result-bg grid grid-cols-2 gap-5" v-if="!resultClicked">
                <div v-for="(result , resultIndex) in searchResult"             :key="`search-result_${resultIndex}`"
                class="shadow-md px-3 flex flex-col rounded-xl bg-white"
                @click="resultClicked=true"
                >
                    <img :src="result.image" class="result-img mx-auto my-2" alt="result-img">
                    <span v-text="result.name" class="mb-2" />
                    <span v-text="`USD ${result.price}`"/>

                    <div class="info mt-5 mb-3 flex items-center justify-between text-sm">
                        <span class="rating flex items-center ">
                            <img src="vectors/rating.svg" class="mr-1" alt="rating">
                            {{result.rating}}
                        </span>
                        <span class="reviews flex items-center">
                            {{result.reviews}} Reviews
                        </span>
                        <img src="vectors/more.svg" alt="more">
                    </div>
                </div>
            </main>
            <selected-result v-else />
        </template>

        <shopping-cart v-else/>

  </div>
</template>

<script>

import ShoppingCart from '@/components/ShoppingCart'
import SelectedResult from '@/components/SelectedResult'

export default {
  name: 'SearchResult',
  components: {
    ShoppingCart,
    SelectedResult
  },
  data: () => ({
    options: 'Filter,Relevance,Newest,Price'.split(','),
    searchResult: [
      { name: 'TMA-2 HD Wireless', price: 350, image: '/img/tma-2_modular.png', rating: 4.6, reviews: 86 },
      { name: 'TMA-2 HD Wireless', price: 350, image: '/img/tma-2_modular.png', rating: 4.6, reviews: 86 },
      { name: 'TMA-2 HD Wireless', price: 350, image: '/img/tma-2_modular.png', rating: 4.6, reviews: 86 },
      { name: 'TMA-2 HD Wireless', price: 350, image: '/img/tma-2_modular.png', rating: 4.6, reviews: 86 },
      { name: 'TMA-2 HD Wireless', price: 350, image: '/img/tma-2_modular.png', rating: 4.6, reviews: 86 },
      { name: 'TMA-2 HD Wireless', price: 350, image: '/img/tma-2_modular.png', rating: 4.6, reviews: 86 }
    ],
    resultClicked: false,
    showCart: false
  })
}
</script>

<style lang="scss" >
    .search-result{

         .result-bg{
            background:#f3f3f3;

        }
        .result-clicked-bg{
            background:#F6F6F6;
        }
        .result-img{
            height:9.6rem;

        }
   }
</style>
