<template>
    <div class="col-lg-6 col-xl-6">
        <slot name="title"><h3>Untitled</h3></slot>
        <img width="300" height="200" :src="imgSrc" :title="imgTitle" v-if="imgSrc">
        <!--<p>{{date || "today"}}</p>-->
        <slot name="caption" :date="date"><p>unkown date</p></slot>
        </div>
</template>

<script>
import axios from 'axios';
    export default {
    props: ['date'],
    data: function(){
        return {
        // greeting: 'Hello Mazzo from Vue Glory!',
        imgSrc: '',
        imgTitle: ''
        }
    },
    created: function(){
       
        this.fetchApod();
    },

    methods:{
            fetchApod: function(){
                var apiKey = 'WjNITMO5uO6l4E0HeLKxmwdmF25SdRn4KXcsxDbY';
                var url = 'https://api.nasa.gov/planetary/apod?api_key=' + apiKey;
                 

                if(this.date){
                    url += '&date=' + this.date;
                }
            
                axios.get(url)
                    .then(res => {
                        // console.clear();
                        console.log(res);
                        this.imgSrc = res.data.url;
                        this.imgTitle = res.data.title;
                    });
            }   
        } //End methods
 }//End export default
</script>
