<template>
  <div class="font-sans bg-gray-100">
    <div class="p-4 mx-auto lg:max-w-7xl sm:max-w-full">
      <h2 class="text-4xl font-extrabold text-gray-800 mb-12">Premium Sneakers</h2>

      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
        <div v-for="(product, index) in filteredProducts" :key="index" class="bg-white rounded-2xl p-5 cursor-pointer hover:-translate-y-2 transition-all relative">
          <a :href="product.url" target="_blank" rel="noopener noreferrer">
            <div class="bg-gray-100 w-10 h-10 flex items-center justify-center rounded-full cursor-pointer absolute top-4 right-4">
              <svg @click="toggleWishlist(product)" xmlns="http://www.w3.org/2000/svg" width="16px" class="fill-red-500 inline-block" viewBox="0 0 64 64" aria-label="Toggle Wishlist">
                <path d="M45.5 4A18.53 18.53 0 0 0 32 9.86 18.5 18.5 0 0 0 0 22.5C0 40.92 29.71 59 31 59.71a2 2 0 0 0 2.06 0C34.29 59 64 40.92 64 22.5A18.52 18.52 0 0 0 45.5 4ZM32 55.64C26.83 52.34 4 36.92 4 22.5a14.5 14.5 0 0 1 26.36-8.33 2 2 0 0 0 3.27 0A14.5 14.5 0 0 1 60 22.5c0 14.41-22.83 29.83-28 33.14Z" />
              </svg>
            </div>

            <div class="w-5/6 h-48 overflow-hidden mx-auto aspect-w-16 aspect-h-8 md:mb-2 mb-4">
              <img :src="product.image" :alt="product.name" class="h-full w-full object-contain" />
            </div>

            <div>
              <h3 class="text-lg font-extrabold text-gray-800">{{ product.name }}</h3>
              <p class="text-gray-600 text-sm mt-2">{{ product.description }}</p>
              <p class="text-gray-800 font-bold mt-2" >{{ product.price }}</p>
            </div>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    searchTerm: {
      type: String,
      required: false,

      default: ''
    }
  },
  data() {
    return {
       products: [
        {
          name: 'Air Jordan 1 Retro High',
          description: 'he Air Jordan 1 Retro High remakes the classic sneaker,',
          price: 'Rp 2.300.000,00',
          image: '/jordan.jpg',
          isInWishlist: false
        },
        {
          name: 'nike vaporfly 3',
          description: 'You can wear it for fast workouts, too, but if an everyday running shoe is what youre after, get something else.',
          price: 'Rp 2.888.000,00',
          image: '/Nike.jpg',
          isInWishlist: false
        },
        {
          name: 'Velvet Boots',
          description: 'Most boots mainly cover the foot and the ankle, while some also cover some part of the lower calf.',
          price: 'Rp 10.000.000,00',
          image: 'https://readymadeui.com/images/product11.webp',
          isInWishlist: false
        },
        {
          name: 'Summit Hiking',
          description: 'used for hiking activities such as trekking or mountain climbing.',
          price: 'Rp 14.000.000,00',
          image: 'https://readymadeui.com/images/product12.webp',
          isInWishlist: false
        },
        {
          name: 'Zenith Glow',
          description: 'Firm ground football shoes are usually used on fields with natural grass, where the ground is medium textured (between hard and wet). FG football boots have four studs at the back and nine studs at the front.',
          price: 'Rp 15.000.000,00',
          image: 'https://readymadeui.com/images/product13.webp',
          isInWishlist: false
        },
        {
          name: 'Echo Elegance',
          description: 'Discover the epitome of sophistication with Echo Elegance, where timeless design meets modern comfort. Perfect for any stylish wardrobe, these shoes are crafted for those who appreciate the finer things in life.',
          price: 'Rp 14.000.000,00',
          image: 'https://readymadeui.com/images/product14.webp',
          isInWishlist: false
        },
        {
          name: 'Pumps',
          description: 'Elevate your style with the  Pumps, where sophistication meets comfort. Designed for the modern woman, these pumps are perfect for any occasion, from the office to an evening out.',
          price: 'Rp 14.000.000,00',
          image: 'https://readymadeui.com/images/product15.webp',
          isInWishlist: false
        },
        {
          name: 'Blaze Burst',
          description: 'Unleash your potential with Blaze Burst, the perfect blend of style and performance. These shoes are designed for those who demand both fashion and functionality.',
          price: 'Rp 14.000.000,00',
          image: 'https://readymadeui.com/images/product10.webp',
          isInWishlist: false
        }
      ]
    };
  },
  computed: {
    filteredProducts() {
      if (!this.searchTerm) {
        return this.products;
      }
      return this.products.filter(product =>
        product.name.toLowerCase().includes(this.searchTerm.toLowerCase())
      );
    }
  },
  methods: {
    
    toggleWishlist(product) {
      product.isInWishlist = !product.isInWishlist;
    }
  }

};
</script>

<style scoped>
/* Styling untuk komponen ini */
</style>
