<template>
  <div id="app">
    <NavBar @search="handleSearch" />
    <DatatablePage :users="filteredUsers" /> 
   </div>
</template>

<script>
import NavBar from './components/NavBar.vue'
import DatatablePage from './components/DatatablePage.vue'
import {users} from './components/userData.js:'

export default {
  name: 'App',
  components: {
    NavBar,
    DatatablePage,
  },
  data() {
    return {
      users: users,
      searchText: '',
    };
  },
  computed: {
    filteredUsers() {
      if (!this.searchText) {
        return this.users;
      }
      const searchLower = this.searchText.toLowerCase();
      return this.users.filter(user =>
        user.username.toLowerCase().includes(searchLower)
      );
    },
  },
  methods: {
    handleSearch(searchText) {
      this.searchText = searchText;
    },
  },
};
</script>

<style>


#app {
  font-family: 'Avenir', 'Helvetica', 'Arial', sans-serif;
  margin: 20px;
  
}
</style>
