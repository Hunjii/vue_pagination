<template>
  <div id="app">
    <home />
    <pagination />
  </div>
</template>

<script>
import Home from './components/Home';
import Pagination from './components/Pagination';
export default {
  name: 'App',
  components: {
    Home,
    Pagination,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
