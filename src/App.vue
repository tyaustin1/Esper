<template>
  <div id="app">
    <card-search/>
  </div>
</template>

<script>
import CardSearch from './components/CardSearch.vue'

export default {
  name: 'App',
  components: {
    CardSearch
  }
}
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
