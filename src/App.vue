<template>
  <div id="app">

  <AsteroidGrid @remove="remove" :asteroids="asteroids" header="Near-Earth Objects"/>

  <!-- <Apod>
    <h3 slot="title">#1</h3>
    <p slot="caption">Here' today's Astronomy Picture of the Day</p>
  </Apod>

  <Apod date="2018-08-07">
    <h3 slot="title">#2</h3>
    <p slot="caption" slot-scope="pic">Here's the picture from {{pic.date}}</p>
  </Apod> -->

  </div>
</template>

<script>
import AsteroidGrid from './components/AsteroidGrid.vue'
 //import Apod from './components/Apod.vue'
import axios from 'axios'

export default {
    name: 'app',
    components: {
    // HelloWorld
      AsteroidGrid
      //Apod
    
    },
    data() {
      return{
        asteroids: [],
        showSummary:true
        }
      
    },
    created: function(){
        this.fetchAsteroids();
        //this.fetchApod();
    },

    methods: {
        fetchAsteroids:function(){
            var apiKey = 'WjNITMO5uO6l4E0HeLKxmwdmF25SdRn4KXcsxDbY';
            var url = 'https://cors-anywhere.herokuapp.com/http://737798.youcanlearnit.net/neos.json';
            axios.get(url)
                .then(res => {
                    console.clear();
                    console.log(res);
                    this.asteroids = res.data.near_earth_objects.slice(0,10);
                    //vm.asteroids = res.data.near_earth_objects.slice(0,10);
                });
        },
        
        remove:function(index){
            //this.$emit('remove', index);
            this.asteroids.splice(index,1);
            // this.asteroids = [];
        }
        // fetchApod: function(){
        //           var apiKey = 'WjNITMO5uO6l4E0HeLKxmwdmF25SdRn4KXcsxDbY';
        //           var url = 'https://api.nasa.gov/planetary/apod?api_key=' + apiKey;
                  

        //           if(this.date){
        //               url += '&date=' + this.date;
        //           }
        //          var self = this;
        //           axios.get(url)
        //               .then(function (res) {
        //                   console.clear();
        //                   console.log(res);
        //                   self.imgSrc = res.data.url;
        //                   self.imgTitle = res.data.title;
        //               });
        //       }   
    }//end methods
}//end export default
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
