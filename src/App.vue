<template>
  <div id="app">
    <WikiHome/>
  </div>
</template>

<script>
import WikiHome from './components/WikiHome.vue';
import VueRouter from 'vue-router';
import SearchWiki from './components/SearchWiki.vue';

const routes = [

  { path: '/', component: WikiHome, name: 'Home' },
  { path: '/search/:searchTerm', component: SearchWiki, name: 'SearchWiki' },


]

export default {
  name: 'App',
  
  components: {
    WikiHome,
},
  //define the route
  router: new VueRouter({ routes, mode: 'history',  })

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
