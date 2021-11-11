<template>
  <v-app id="inspire" :style="{background: $vuetify.theme.themes.dark.background}">
    <v-container>
      
      
    <carousel-3d :controls-visible="true" :clickable="false" :height="300">
      <slide :index="i" :key="i" v-for="(slide, i) in slides">
        <figure>
          <img :src="slide.src" />
          <figcaption>
            <v-btn text color="white">{{slide.text}}</v-btn>
          </figcaption>
        </figure>
        </slide> 
    </carousel-3d>

   
    
    </v-container>
  </v-app>
</template>

<script>

import {Carousel3d, Slide} from "vue-carousel-3d"
  export default {
    name: 'main',
    data: () => ({
      slides: [
        {src: require('../../public/img1.png'), text:'111'},
        {src: require('../../public/img1.png'), text:'222'},
        {src: require('../../public/img1.png'), text:'333'}
        
      ]
    }),
    components: {
    Carousel3d,
    Slide
    },
  }
</script>
<style>
.carousel-3d-container figure {
  margin: 0;
}
.carousel-3d-container figcaption {
  position: absolute;
  background-color: rgba(0, 0, 0, 0.5);
  color: white;
  bottom: 0;
  position: absolute;
  bottom: 0;
  padding: 15px;
  font-size: 12px;
  min-width: 100%;
  box-sizing: border-box;
}
.next span,
.prev span {
  color: orange;
}
</style>