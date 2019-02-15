<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->

  <AsteroidGrid @remove="remove" :asteroids="asteroids" header="Near-Earth Objects"/>

  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import AsteroidGrid from './components/AsteroidGrid.vue'
import axios from 'axios'

export default {
  name: 'app',
  components: {
  // HelloWorld
    AsteroidGrid
  },
  data() {
    return{
      asteroids: []
      }
    
  },
  created: function(){
      this.fetchAsteroids();
  },

  methods: {
      fetchAsteroids:function(){
          var apiKey = 'WjNITMO5uO6l4E0HeLKxmwdmF25SdRn4KXcsxDbY';
          var url = 'http://737798.youcanlearnit.net/neos.json';
          axios.get(url)
              .then(res => {
                  console.clear();
                  console.log(res);
                  this.asteroids = res.data.near_earth_objects.slice(0,10);
              });
      }
  }
}
</script>

<style>
/* #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */

 [v-cloak] {
        display: none;
    }
</style>
