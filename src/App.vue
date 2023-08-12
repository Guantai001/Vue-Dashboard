<template>
  <div id="app">
    <NavBar @search="handleSearch" />
    <DatatablePage :users="filteredUsers" @delete-user="deleteUser" /> 
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
      lableType: '',
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

      if (this.lableType) {
        filteredUsers = filteredUsers.filter(user => user.lable === this.lableType);
      }

      if (this.statusType) {
        filteredUsers = filteredUsers.filter(user => user.status === this.statusType);
      }

      return filteredUsers;
    },
  },
  methods: {
    handleSearch(searchText, accessType, statusType, lableType) {
      this.searchText = searchText;
      this.accessType = accessType;
      this.statusType = statusType;
      this.lableType = lableType;
    },
      deleteUser(userToDelete) {
    // Find the index of the user to delete in the users array
    const indexToDelete = this.users.findIndex(user => user.id === userToDelete.id);

    if (indexToDelete !== -1) {
      // Remove the user from the users array
      this.users.splice(indexToDelete, 1);
    }
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

