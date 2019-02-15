<template>
    <div class="col-lg-6 col-xl-6">
        <slot name="title"><h3>Untitled</h3></slot>
        <img width="300" height="200" :src="imgSrc" :title="imgTitle">
        <!--<p>{{date || "today"}}</p>-->
        <slot name="caption" :date="date"><p>unkown date</p></slot>
</template>

<script>
    export default {

    props: ['date'],
    data: function(){
        return {
        // greeting: 'Hello Mazzo from Vue Glory!',
        imgSrc: '',
        imgTitle: ''
        }
    },
    methods:{
            // fetchApod: function(){
            //     var apiKey = 'WjNITMO5uO6l4E0HeLKxmwdmF25SdRn4KXcsxDbY';
            //     var url = 'https://api.nasa.gov/planetary/apod?api_key=' + apiKey;
                 

            //     if(this.date){
            //         url += '&date=' + this.date;
            //     }
            //    var self = this;
            //     axios.get(url)
            //         .then(function (res) {
            //             console.clear();
            //             console.log(res);
            //             self.imgSrc = res.data.url;
            //             self.imgTitle = res.data.title;
            //         });
            // }   
        } //End methods
 }//End export default
</script>
