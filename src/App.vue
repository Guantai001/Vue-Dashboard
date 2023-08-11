<template>
  <div id="app">
    <NavBar @search="handleSearch" />
    <DatatablePage :users="filteredUsers" /> 
   </div>
</template>


<script>
import NavBar from './components/NavBar.vue';
import DatatablePage from './components/DatatablePage.vue';
import { users } from './components/userData.js:';

export default {
  name: 'App',
  components: {
    NavBar,
    DatatablePage,
  },
  data() {
    return {
      users: users,
      searchText: '', // Change this from searchUsername to searchText
      accessType: '',
      statusType: '',
    };
  },
  computed: {
    filteredUsers() {
      let filteredUsers = this.users;
      if (this.searchText) { // Change this from searchUsername to searchText
        const searchLower = this.searchText.toLowerCase();
        filteredUsers = filteredUsers.filter(
          user => user.username.toLowerCase().includes(searchLower)
        );
      }

      if (this.accessType) {
        filteredUsers = filteredUsers.filter(user => user.access === this.accessType);
      }

      if (this.statusType) {
        filteredUsers = filteredUsers.filter(user => user.status === this.statusType);
      }

      return filteredUsers;
    },
  },
  methods: {
    handleSearch(searchText, accessType, statusType) {
      this.searchText = searchText;
      this.accessType = accessType;
      this.statusType = statusType;
    },
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
   margin: 30px;
}
</style>

