<template>
  <div class="sliderAx h-auto relative">
 
    <div v-for="(slide, index) in slides" :key="index" class="container mx-auto" v-show="currentSlide === index">
      <div
        class="bg-cover bg-center h-auto text-white py-24 px-10 object-fill"
        :style="{ backgroundImage: `url(${slide.image})` }"
      >
        <div class="md:w-1/2">
          <p class="font-bold text-sm uppercase">{{ slide.title }}</p>
          <p class="text-3xl font-bold">{{ slide.heading }}</p>
          <p class="text-2xl mb-10 leading-none">{{ slide.description }}</p>
          <a
            href="#"
            class="bg-purple-800 py-4 px-8 text-white font-bold uppercase text-xs rounded hover:bg-gray-200 hover:text-gray-800"
            >Contact us</a
          >
        </div>
      </div>
      <br />
    </div>
    <div class="flex justify-center space-x-4 mx-auto pb-2">
      <button
        v-for="(slide, index) in slides"
        :key="index"
        :class="{'bg-purple-800': currentSlide === index, 'bg-purple-400': currentSlide !== index}"
        @click="goToSlide(index)"
        class="rounded-full w-4 h-4"
       ></button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      slides: [
        {
          title: 'Shoes',
          heading: 'All world',
          description: '“Nikmati Keunikannya! Pesan Sekarang sepatu di DimStore”',
          image:
            'tes.jpg',
        },
        
        {
          title: 'cari sepatu',
          description: 'Bingung cari sepatu yang murah dan bagus? cari aja di DimStore tunggu apa lagi!!!  ',
          image:
            '/sepatu.webp',
        },
      ],
      currentSlide: 0,
      interval: null,
    };
  },
  methods: {
    goToSlide(index) {
      this.currentSlide = index;
      this.resetInterval();
    },
    loopSlider() {
      this.interval = setInterval(() => {
        this.currentSlide =
          (this.currentSlide + 1) % this.slides.length;
      }, 8000);
    },
    resetInterval() {
      clearInterval(this.interval);
      this.loopSlider();
    },
  },
  mounted() {
    this.loopSlider();
  },
  beforeUnmount() {
    clearInterval(this.interval);
  },
};
</script>

<style scoped>
.sliderAx {
  position: relative;
}
</style>
