<template>
    <main class="flex flex-col">
        <div class="flex items-center justify-between px-5">
            <span class="text-xl">Headphone</span>
            <span class="">Remove</span>
        </div>

    </main>
</template>

<script>
export default {
  name: 'ShoppingCart',
  data: () => ({
    items: [
      { image: 'img/', name: 'TMA-2 Comfort Wireless ', price: 270, qty: 1 },
      { image: 'img/', name: ' ', price: 270, qty: 1 }
    ]
  })
}
</script>
