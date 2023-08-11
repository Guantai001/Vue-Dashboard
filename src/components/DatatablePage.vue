<template>
    <div class="relative mt-10">
    <table class="w-full text-sm text-left text-gray-500 ">
        <thead class="text-xs text-gray-700 uppercase ">
            <tr>
            <th scope="col" class="px-6 py-3">
                  User
                </th>
                <th scope="col" class="px-6 py-3">
                   Username/USSD
                </th>
                <th scope="col" class="px-6 py-3">
                   Access
                </th>
                 <th scope="col" class="px-6 py-3">
                   Group
                </th>
                 <th scope="col" class="px-6 py-3">
                   Status
                </th>
                 <th scope="col" class="px-6 py-3">
                   Action
                </th>
            </tr>
          </thead>
          <tbody>
            <tr class="bg-white border-b " v-for="user in paginatedUsers" :key="user.id">
              <td class="px-6 py-4">{{ user.name }}</td>
              <td class="px-6 py-4">{{ user.username }}</td>
              <td class="px-6 py-4">{{ user.access }}</td>
               <td class="px-6 py-4">{{ user.group }}</td>
                <td class="px-6 py-4">{{ user.status }}</td>
                <td class="px-6 py-4">{{ user.action }}</td>
            </tr>
          </tbody>
        </table>
        </div>
         <div class='flex m-4 justify-end'>
         <div class='flex  justify-between mx-20'>
        <p class="p-2">Show</p>
          <select class="p-2 bg-white border" v-model="itemsPerPage" @change="changeItemsPerPage">
          <option v-for="option in itemsPerPageOptions" :value="option" :key="option">{{ option }}</option>
        </select> 
        <p class="p-2">Entries</p>
        </div>
       <nav aria-label="Page navigation">
          <ul class="pagination flex mt-2 mx-4">
            <li class="page-item mx-2">
              <a class="page-link" href="#" @click.prevent="prevPage">Previous</a>
            </li>
            <li class="page-item mx-2" v-for="page in [currentPage]" :key="page" :class="{ 'active': currentPage === page }">
              <a class="page-link" href="#" @click.prevent="gotoPage(page)">{{ page }}</a>
            </li>
            <li class="page-item mx-2">
              <a class="page-link" href="#" @click.prevent="nextPage">Next</a>
            </li>
          </ul>
        </nav>
        </div>

</template>


<script>

export default {
  props: {
    users:Array
  },
  data() {
    return {
      itemsPerPageOptions: [5, 10, 20],
      itemsPerPage: 5,
      currentPage: 1,
    };
  },
  computed: {
    paginatedUsers() {
      const startIndex = (this.currentPage - 1) * this.itemsPerPage;
      const endIndex = startIndex + this.itemsPerPage;
      return this.users.slice(startIndex, endIndex);
    },
    totalPages() {
      return Math.ceil(this.users.length / this.itemsPerPage);
    },
  },
  methods: {
    prevPage() {
      if (this.currentPage > 1) {
        this.currentPage--;
      }
    },
    nextPage() {
      if (this.currentPage < this.totalPages) {
        this.currentPage++;
      }
    },
    gotoPage(page) {
      this.currentPage = page;
    },
    changeItemsPerPage() {
      this.currentPage = 1; 
    },
  },
};
</script>