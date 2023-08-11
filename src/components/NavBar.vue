<template>
  <div class="flex justify-between  mt-5">
    <div class="flex flex-col">
      <h1 class="text-2xl font-bold text-black">User Listing</h1>
      <p class="text-lg font-regular text-grey">User Listing</p>
    </div>
    <input 
        type="text" 
        class="h-10 px-3 pr-8 text-sm text-grey-darker border rounded ountline-none mt-5 focus:outline-none focus:shadow-outline" 
        placeholder="Search by name"
    />
  </div>
  <div class="flex mt-10 justify-between">
  <div class="flex ">
  <select class="block appearance-none bg-white border border-grey-light hover:border-grey px-4 py-2 pr-8 rounded  mx-4 leading-tight focus:outline-none focus:shadow-outline">
    <option>Sort by</option>
    <option>Ascending</option>
    <option>Descending</option>
    </select>
      <select class="block appearance-none bg-white border border-grey-light hover:border-grey px-4 py-2 pr-8 rounded mr-4  leading-tight focus:outline-none focus:shadow-outline">
    <option>Sort by</option>
    <option>Ascending</option>
    <option>Descending</option>
    </select>
      <select class="block appearance-none bg-white border border-grey-light hover:border-grey px-4 py-2 pr-8 rounded  leading-tight focus:outline-none focus:shadow-outline">
    <option>Sort by</option>
    <option>Ascending</option>
    <option>Descending</option>
    </select>
    </div>
      <div class="flex ">
  <select class="block appearance-none bg-white border border-grey-light hover:border-grey px-4 py-2 pr-8 rounded  mx-4 leading-tight focus:outline-none focus:shadow-outline">
    <option>Sort by</option>
    <option>Ascending</option>
    <option>Descending</option>
    </select>
    <select class="block appearance-none bg-white border border-grey-light hover:border-grey px-4 py-2 pr-8 rounded  mx-4 leading-tight focus:outline-none focus:shadow-outline">
    <option>Sort by</option>
    <option>Ascending</option>
    <option>Descending</option>
    </select>
    </div>
  </div>
</template>

<script>
export default {
  name: 'UserListing'
};
</script>

<style scoped>
/* Add your scoped styles here */
</style>
