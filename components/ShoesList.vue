<template>
  <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
    <div v-for="shoe in filteredShoes" :key="shoe.id" class="border p-4 rounded">
      <NuxtLink :href="shoe.url">
        <img :src="shoe.image" :alt="shoe.name" class="w-full h-48 object-cover mb-4 rounded" />
        <h2 class="text-lg font-semibold mb-2">{{ shoe.name }}</h2>
        <p class="text-gray-600">{{ shoe.description }}</p>
        <p class="text-gray-800 font-bold">{{ shoe.price.toLocaleString('id-ID', { style: 'currency', currency: 'IDR' }) }}</p>
        <p class="text-gray-600">Available Colors: {{ shoe.colors.join(', ') }}</p>
      </NuxtLink>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const shoes = ref([
  {
    id: 1,
    name: 'Nike Air Max',
    description: 'Comfortable and stylish',
    price: 1500000,
    url: '/shoes/nike-air-max',
    image: 'https://via.placeholder.com/150',
    colors: ['Red', 'Blue', 'Green']
  },
  {
    id: 2,
    name: 'Adidas Ultraboost',
    description: 'Boost your run',
    price: 1800000,
    url: '/shoes/adidas-ultraboost',
    image: 'https://via.placeholder.com/150',
    colors: ['Black', 'White']
  },
  // Add more shoes...
]);

const searchTerm = ref("");

const filteredShoes = computed(() => {
  if (!searchTerm.value) {
    return shoes.value;
  }
  return shoes.value.filter(shoe =>
    shoe.name.toLowerCase().includes(searchTerm.value.toLowerCase()) ||
    shoe.description.toLowerCase().includes(searchTerm.value.toLowerCase())
  );
});
</script>
