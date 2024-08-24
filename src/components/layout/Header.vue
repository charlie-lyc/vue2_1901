<template>
  <header class="header">

    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/todos">Todos</router-link> 
    </nav> 

    <!-- <h1>Todo List</h1> -->
    
  </header>
</template>

<script>
  export default {
    name: 'HeaderVue'
  }
</script>

<style scoped>
 .header {
    background: #333;
    color: #fff;
    text-align: center;
    padding: 10px;
 }
 .header a {
    color: #fff;
    padding-right: 5px;
 }
</style>