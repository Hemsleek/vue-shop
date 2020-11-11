<template>
    <main class="bg-white">
        <header class="flex items-center justify-between h-20 px-10 text-lg">
            <span v-for="(tab, tabIndex) in tabs"
            :class="`flex flex-col cursor-pointer ${activeTab===tab? 'mt-3' : ''}`"
            @click="activeTab=tab"
            :key="`selected-result_${tabIndex}`">
                {{tab}}
                <span class="bg-green-500 w-6 h-1 mt-2 mx-auto" v-if="handleActiveTab(tab)" />
            </span>
        </header>

        <main class="flex justify-between pl-10 mt-3" v-if="handleActiveTab('Overview')">
            <span class=" image-large flex items-center justify-center result-bg mr-6 shadow rounded-lg">
                <img src="img/tma_2-HDwireless.png" alt="tma2-HD">
            </span>
            <img src="img/tma_2-half.png" alt="tma-half">
        </main>

        <main class="mt-3 flex flex-col pl-10" v-if="handleActiveTab('Features')">
            <div class="feature font-bold text-xl">Highly Detailed Audio</div>
            <p class="mt-4 mb-4 font-normal text-md pr-6">
                The speaker unit contains a diaphragm that is precision-grown from NAC Audio bio-cellulose, making it stiffer, lighter and stronger than regular PET speaker units, and allowing the sound-producing diaphragm to vibrate without the levels of distortion found in other speakers.
            </p>
            <div :class="`flex w-10/12 ${featureIndex===1? 'mt-6' : ''}`"
                v-for="(feature, featureIndex) in features"
                :key="`searchresult-feature${featureIndex}`"
            >
                <img :src="feature.image" alt="image">
                <div class="flex-grow flex flex-col ml-4">
                    <span :class="`font-bold text-xl  ${featureIndex===1? 'mb-2' : 'mb-3'}`" v-text="feature.title" />
                    <p v-text="feature.text" />
                </div>
            </div>
        </main>

        <span class="flex items-center justify-center ml-10 w-4/5 h-16 my-green text-white my-6 rounded-md cursor-pointer font-bold text-md">Add To Cart</span>
    </main>
</template>

<script>

export default {
  name: 'SelectedResult',
  data: () => ({
    tabs: 'Overview,Features,Specification'.split(','),
    features: [
      { image: 'img/APTX.png', title: 'APTX HD WIRELESS AUDIO', text: 'The Aptx® HD codec transmits 24-bit hi-res audio, equal to or better than CD quality.' },
      { image: 'img/ultra-soft.png', title: 'ULTRA SOFT WITH ALCANTARA', text: 'Alcantara® is a highly innovative material offering an unrivalled combination of' }
    ],
    activeTab: 'Overview'

  }),

  methods: {
    handleActiveTab (tab) { return tab === this.activeTab }

  }
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
