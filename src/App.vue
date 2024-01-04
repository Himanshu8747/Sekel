<template>
  <h1>Sekel Assignment</h1>
  <Get_All_PostsVue/>
</template>

<script>
import Get_All_PostsVue from './components/Get_All_Posts.vue'
export default {
  name: 'App',
  components: {
    Get_All_PostsVue,
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
