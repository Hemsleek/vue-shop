<template>
    <main class="  flex flex-col">
        <div class="flex items-center justify-between px-5">
            <span class="text-xl">Headphone</span>
            <span class="">Remove</span>
        </div>

        <div class="flex-grow flex flex-col mt-6 pl-5 w-10/12">
            <div class="flex mb-6"
                v-for="(item, itemIndex) in items"
                :key="`cart-item${itemIndex}`"
            >
                <div class="flex items-center justify-center rounded-lg result-clicked-bg">
                    <img :src="item.image" class="w-32 h-32 object-cover" alt="item-img">
                </div>
                <div class="flex flex-col ml-5 flex-grow">
                    <span class="text-xl" v-text="item.name" />
                    <span class="mt-2 text-lg font-bold" v-text="`USD ${item.price}`" />
                    <span class="mt-6 flex justify-between items-center text-lg">
                        Qty {{item.qty}}
                        <img src="vectors/delete.svg" class="w-8 h-8" alt="delete-icon">
                    </span>
                </div>
            </div>
        </div>

        <div class="flex justify-between items-center h-16 mt-48  px-6">
            <span class="text-lg">Total 2 items</span>
            <span class="text-2xl font-bold">USD 295</span>
        </div>
        <div class="px-5 h-48 flex items-center result-clicked-bg">

            <span class="flex items-center justify-between px-6  w-full h-16 my-green text-white my-6 rounded-md cursor-pointer font-bold text-lg">
                Proceed to Checkout
                <img  class="w-6 h-6" src="vectors/arrow-right.svg" alt="arrow-right">
            </span>
        </div>
    </main>
</template>

<script>
export default {
  name: 'ShoppingCart',
  data: () => ({
    items: [
      { image: '/img/tma-2_modular.png', name: 'TMA-2 Comfort Wireless', price: 270, qty: 1 },
      { image: '/img/co2_cable.png', name: 'C02 - Cable', price: 25, qty: 1 }
    ]
  })
}
</script>
<style lang="scss" scoped>
    .my-green{
        background:#0ACF83;

    }
</style>
