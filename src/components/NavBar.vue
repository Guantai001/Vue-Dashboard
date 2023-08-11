<template>
  <div class="flex justify-between  mt-5">
    <div class="flex flex-col">
      <h1 class="text-2xl font-bold text-black">User Listing</h1>
      <p class="text-lg font-regular text-grey">User Listing</p>
    </div>
   <input
      type="text"
      class="h-10 px-3 pr-8 text-sm text-grey-darker border rounded outline-none mt-5 focus:outline-none focus:shadow-outline"
      placeholder="Search by name"
      v-model="searchText"
      @input="handleSearch"
    />

  </div>
</template>

<script>
export default {
  name: 'NavBar',
  data() {
    return {
      searchText: '',
    };
  },
  methods: {
    handleSearch() {
      this.$emit('search', this.searchText);
    },
  },
};
</script>

