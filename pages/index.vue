<template>
    <Navbar @update:searchTerm="updateSearchTerm" />
    <Carousel />
    <Inacative />
    <ProductList :searchTerm="searchTerm" />
    <ProductRating />
</template>

<script>

export default {
  data() {
    return {
      searchTerm: ''
    };
  },
  methods: {
    updateSearchTerm(term) {
      this.searchTerm = term;
    }
  }
};
</script>