<template>
    <main class="bg-white">
        <header class="flex items-center justify-between h-20 px-10 text-lg">
            <span v-for="(tab, tabIndex) in tabs"
            :key="`selected-result_${tabIndex}`">
                {{tab}}
            </span>
        </header>

        <div class="flex justify-between pl-10 mt-3">
            <span class=" image-large flex items-center justify-center result-bg mr-6 shadow rounded-lg">
                <img src="img/tma_2-HDwireless.png" alt="tma2-HD">
            </span>
            <img src="img/tma_2-half.png" alt="tma-half">
        </div>

        <span class="flex items-center justify-center ml-10 w-4/5 h-16 my-green text-white my-6 rounded-md cursor-pointer font-bold text-md">Add To Cart</span>
    </main>
</template>

<script>

export default {
  name: 'SelectedResult',
  data: () => ({
    tabs: 'Overview,Features,Specification'.split(',')
  })
}
</script>

<style lang="scss" scoped>
    main{

        img[alt="tma2-HD"]{
            width:24rem;
            height:24rem;
            object-fit: contain;
        }
        .image-large{
            height:29rem;
        }
        .my-green{
            background:#0ACF83;
        }
    }
</style>
