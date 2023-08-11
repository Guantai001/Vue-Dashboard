<template>
  <div id="app">
    <NavBar  />
    <DatatablePage /> 
   </div>
</template>

<script>
import NavBar from './components/NavBar.vue'
import DatatablePage from './components/DatatablePage.vue'


export default {
  name: 'App',
  components: {
    NavBar,
    DatatablePage
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', 'Helvetica', 'Arial', sans-serif;
  margin: 20px;
  
}
</style>
