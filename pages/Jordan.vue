<template>
  <section class="relative">
    <div class="w-full mx-auto px-4 sm:px-6 lg:px-0">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 mx-auto max-md:px-2">
        <div class="img">
          <div class="img-box h-full max-lg:mx-auto">
            <img
              :src="product.imageUrl"
              :alt="product.name + ' image'"
              class="max-lg:mx-auto lg:ml-auto h-full"
            />
          </div>
        </div>
        <div
          class="data w-full lg:pr-8 pr-0 xl:justify-start justify-center flex items-center max-lg:pb-10 xl:my-2 lg:my-5 my-0"
        >
          <div class="data w-full max-w-xl">
            <p class="text-lg font-medium leading-8 text-indigo-600 mb-4">
              {{ product.category }}&nbsp; /&nbsp; {{ product.subcategory }}
            </p>
            <h2
              class="font-manrope font-bold text-3xl leading-10 text-gray-900 mb-2 capitalize"
            >
              {{ product.name }}
            </h2>
            <div class="flex flex-col sm:flex-row sm:items-center mb-6">
              <h6
                class="font-manrope font-semibold text-2xl leading-9 text-gray-900 pr-5 sm:border-r border-gray-200 mr-5"
              >
                {{ formatPrice(product.price) }}
              </h6>
              <div class="flex items-center gap-2">
                <!-- Rating icons -->
                <div class="flex items-center gap-1">
                  <svg
                    v-for="star in product.rating"
                    :key="star"
                    width="20"
                    height="20"
                    viewBox="0 0 20 20"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                    class="text-yellow-500"
                  >
                    <path
                      d="M9.10326 2.31699C9.47008 1.57374 10.5299 1.57374 10.8967 2.31699L12.7063 5.98347C12.8519 6.27862 13.1335 6.48319 13.4592 6.53051L17.5054 7.11846C18.3256 7.23765 18.6531 8.24562 18.0596 8.82416L15.1318 11.6781C14.8961 11.9079 14.7885 12.2389 14.8442 12.5632L15.5353 16.5931C15.6754 17.41 14.818 18.033 14.0844 17.6473L10.4653 15.7446C10.174 15.5915 9.82598 15.5915 9.53466 15.7446L5.91562 17.6473C5.18199 18.033 4.32456 17.41 4.46467 16.5931L5.15585 12.5632C5.21148 12.2389 5.10393 11.9079 4.86825 11.6781L1.94038 8.82416C1.34687 8.24562 1.67438 7.23765 2.4946 7.11846L6.54081 6.53051C6.86652 6.48319 7.14808 6.27862 7.29374 5.98347L9.10326 2.31699Z"
                      fill="#FBBF24"
                    />
                  </svg>
                </div>
                <span class="pl-2 font-normal leading-7 text-gray-500 text-sm"
                  >{{ product.reviews.length }} reviews</span
                >
              </div>
            </div>
            <p class="text-gray-500 text-base font-normal mb-5">
              {{ product.description }}
              <a href="#" class="text-indigo-600">More....</a>
            </p>
            <ul class="grid gap-y-4 mb-8">
              <li v-for="(feature, index) in product.features" :key="index" class="flex items-center gap-3">
                <svg
                  width="26"
                  height="26"
                  viewBox="0 0 26 26"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                  class="text-gray-900"
                >
                  <rect width="26" height="26" rx="13" fill="#4F46E5" />
                  <path
                    d="M7.66669 12.629L10.4289 15.3913C10.8734 15.8357 11.0956 16.0579 11.3718 16.0579C11.6479 16.0579 11.8701 15.8357 12.3146 15.3913L18.334 9.37183"
                    stroke="white"
                    stroke-width="1.6"
                    stroke-linecap="round"
                  />
                </svg>
                <span class="font-normal text-base text-gray-900">{{ feature }}</span>
              </li>
            </ul>
            <p class="text-gray-900 text-lg leading-8 font-medium mb-4">Size</p>
            <div class="w-full pb-8 border-b border-gray-100 flex-wrap">
              <div
                class="grid grid-cols-3 min-[400px]:grid-cols-5 gap-3 max-w-md"
              >
                <button
                  v-for="(size, index) in product.sizes"
                  :key="index"
                  @click="selectedSize = size"
                  :class="{
                    'bg-indigo-600 text-white': selectedSize === size,
                    'bg-white text-gray-900': selectedSize !== size,
                  }"
                  class="text-center py-1.5 px-6 w-full font-semibold text-lg leading-8 border border-gray-200 flex items-center rounded-full justify-center transition-all duration-300 hover:bg-gray-50 hover:shadow-sm hover:shadow-gray-100 hover:border-gray-300 visited:border-gray-300 visited:bg-gray-50"
                >
                  {{ size }}
                </button>
              </div>
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3 py-8">
              <div class="flex sm:items-center sm:justify-center w-full">
                <button
                  class="group py-4 px-6 border border-gray-400 rounded-l-full bg-white transition-all duration-300 hover:bg-gray-50 hover:shadow-sm hover:shadow-gray-300"
                  @click="decrementQuantity"
                >
                  <svg
                    class="stroke-gray-900 group-hover:stroke-black"
                    width="22"
                    height="22"
                    viewBox="0 0 22 22"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      d="M16.5 11H5.5"
                      stroke=""
                      stroke-width="1.6"
                      stroke-linecap="round"
                    />
                  </svg>
                </button>
                <input
                  type="number"
                  v-model.number="quantity"
                  class="font-semibold text-gray-900 cursor-pointer text-lg py-[13px] px-6 w-full sm:max-w-[118px] outline-0 border-y border-gray-400 bg-transparent placeholder:text-gray-900 text-center hover:bg-gray-50"
                  placeholder="1"
                  min="1"
                  max="10"
                />
                <button
                  class="group py-4 px-6 border border-gray-400 rounded-r-full bg-white transition-all duration-300 hover:bg-gray-50 hover:shadow-sm hover:shadow-gray-300"
                  @click="incrementQuantity"
                >
                  <svg
                    class="stroke-gray-900 group-hover:stroke-black"
                    width="22"
                    height="22"
                    viewBox="0 0 22 22"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      d="M5.5 11H16.5"
                      stroke=""
                      stroke-width="1.6"
                      stroke-linecap="round"
                    />
                    <path
                      d="M11 5.5V16.5"
                      stroke=""
                      stroke-width="1.6"
                      stroke-linecap="round"
                    />
                  </svg>
                </button>
              </div>
              <button
                class="w-full py-4 font-semibold text-white bg-indigo-600 transition-all duration-300 hover:bg-indigo-700 rounded-lg shadow-lg"
                @click="addToCart"
              >
                Add to Cart
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      product: {
        id: 1,
        name: 'Air Jordan 1 Retro High OG',
        category: 'Shoes',
        subcategory: 'Sneakers',
        price: 2300000,
        imageUrl:'/jordan.jpg',
        rating: 4.5,
        reviews: [
          { id: 1, rating: 5, text: 'Great shoes!' },
          { id: 2, rating: 4, text: 'Comfortable and stylish.' },
        ],
        description: 'The Air Jordan 1 Retro High remakes the classic sneaker, giving you a fresh look with a familiar feel. Premium materials with new colours and textures give modern expression to an all-time favourite. Leather offers durability and structure. Encapsulated Air-Sole units provide lightweight cushioning',
        features: ['Leather upper', 'Rubber outsole', 'Textile lining' , ],
        sizes: ['7', '8', '9', '10', '11'],
      },
      selectedSize: '',
      quantity: 1,
    }; 
  },
  methods: {
    formatPrice(price) {
      // Function to format price to IDR
      return new Intl.NumberFormat('id-ID', {
        style: 'currency',
        currency: 'IDR',
      }).format(price);
    },
    incrementQuantity() {
      if (this.quantity < 10) {
        this.quantity++;
      }
    },
    decrementQuantity() {
      if (this.quantity > 1) {
        this.quantity--;
      }
    },
    addToCart() {
      // Placeholder function to add to cart
      console.log('Added to cart:', {
        productId: this.product.id,
        size: this.selectedSize,
        quantity: this.quantity,
      });

      // Implement your logic to add to cart here

      this.selectedSize = '';
      this.quantity = 1;

      alert('Product added to cart!');

      // Optionally, you can redirect to another page after adding to cart
      // this.$router.push('/cart');
      
    },
  },
};
</script>

<style scoped>
/* Your scoped styles here */
</style>
