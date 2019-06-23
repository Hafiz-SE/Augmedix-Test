<template>
  <div id="app">
    <div class="box-outer"> 
      <div class="box"></div>
        <v-app id="inspire">      

          <v-toolbar id="toolbar" color='transparent' flat >
            <v-toolbar-title><img id="image" :src="images"/></v-toolbar-title>
            <v-toolbar-items class="hidden-sm-and-down">  
              <v-btn v-for="buttons in menu" :key="buttons.title" flat class="text-none" >{{ buttons.title }}</v-btn>
            </v-toolbar-items>
            <v-btn flat  class="hidden-sm-and-down text-none outlined" round color="primary">Request demo</v-btn>
            <v-spacer></v-spacer>
            <v-toolbar-side-icon v-show="!drawer" class="hidden-md-and-up" @click="drawer = !drawer"><v-icon id="toolbarIcon" >menu</v-icon></v-toolbar-side-icon>
          </v-toolbar>

          <v-navigation-drawer temporary app v-model="drawer" disable-resize-watcher class="semiTransparent" color="#003056" right height='100vh' :width='windowSize.x'>
            <v-container>
              <v-layout  justify-end row>
                <v-btn flat fab small color="white" class="mt-4"  @click="drawer=false"><v-icon>fas fa-times</v-icon></v-btn>
              </v-layout>
              <v-layout v-for="buttons in menu" :key="buttons.title" column>
                <button class="blockBtn" color="white">{{buttons.title}}</button>
                <hr color="#005596" size="1">
              </v-layout>
              <div class="navFooter">
                <v-layout align-center justify-space-between row fill-height>
                  <a href="#"><v-icon small color="white">fab fa-facebook-square</v-icon></a>
                  <a href="#"><v-icon small color="white">fab fa-twitter</v-icon></a>
                  <a href="#"><v-icon small color="white">fab fa-linkedin</v-icon></a>
                  <a href="#"><v-icon small color="white">fab fa-youtube</v-icon></a>
                </v-layout>
              </div>
            </v-container>
          </v-navigation-drawer>

          <v-layout align-start justify-space-around column fill-height>
            <div class="content">
              <h2>Rehumanizing Healthcare</h2>        
              <p>Augmedix gives providers a team of real-time, quality-controlled, and customized remote scribes, accessed through Glass. Our productivity platform takes care of many major administrative tasks.</p>
              <v-btn class="hidden-xs-only text-capitalize " round color="primary">Primary Button</v-btn>
              <v-btn  class="hidden-sm-and-up text-capitalize" small round color="primary">Small Button</v-btn>
            </div>
          
            <div class="footer">
              <v-layout align-center justify-space-between row fill-height>
              <a href="#"><v-icon v-show="!drawer" small color="#003056">fab fa-facebook-square</v-icon></a>
              <a href="#"><v-icon v-show="!drawer" small color="#003056">fab fa-twitter</v-icon></a>
              <a href="#"><v-icon v-show="!drawer" small color="#003056">fab fa-linkedin</v-icon></a>
              <a href="#"><v-icon v-show="!drawer" small color="#003056">fab fa-youtube</v-icon></a>
              </v-layout>
            </div>
          </v-layout>

        </v-app>
      </div>
  </div>
</template>

<script>
import Vue from 'vue'
import Vuetify from 'vuetify'
import 'vuetify/dist/vuetify.min.css'

Vue.use(Vuetify)

export default {
  name: 'app',
  data () {
    return {
      menu: [
        { title: 'Remote scribe' },
        { title: 'For providers' },
        { title: 'Updates' },
        { title: 'About' },
        { title: 'Contact' }
      ],
      images: require('./assets/logo.png'),
      drawer: false,
      windowSize: {
        x: 0,
        y: 0
      },
    }
  },
  mounted () {
      this.onResize()
  },
  methods: {
    onResize () {
      this.windowSize = { x: window.innerWidth, y: window.innerHeight }
    },
  }
}
</script>

<style>
/*Global Styles*/
@import url('https://fonts.googleapis.com/css?family=Nunito:400,700|Open+Sans&display=swap');
  h1,h2,h3,h4,h5,h6{
    font-family: 'Nunito', sans-serif;
    font-weight: 700;
    color: #003056;
    padding-left:10px;
  }

  .v-btn.outlined {
    border: 1px solid #288DC1;
    color: #288DC1;
  }

  .semiTransparent {
   background-color: #003056!important;
   opacity: 0.85;
   border-color: transparent!important;
  }

  .content p {
    padding-top:30px;
    padding-bottom: 30px;
    padding-left:10px;
  }

  .blockBtn {
    display: block;
    width: 100%;
    border: none;
    background-color: transparent;
    padding: 10px 10px;
    font-size: 13px;
    cursor: pointer;
    text-align: left;
    color: white;
    font-weight: 900;  
  }

  .blockBtn:hover {
    color: #3587D8;
  }

  .box-outer{
    overflow: hidden;
    position: relative;
    height: auto;
  }

  #inspire{
    font-family: 'Open Sans', sans-serif;
    height: 100%;
  }

  #toolbar{
    padding-top: 40px;
  }

@media only screen and (min-width: 600px) {
  h1,h2,h3,h4,h5,h6{
    font-size: 36px;
  }

  .content {
    width: 500px;
    padding-left: 20px;
    padding-top: 85px;
  }

  .footer{
    padding-top:160px;
    padding-left:30px;
    width: 150px;
  }

  .navFooter{
    padding-top:610px;
    padding-left:15px;
    width: 135px;
  }

  .box {
    position: absolute;
    height: 120%;
    width: 200%;
    right: -180%;
    top: 0%;
    transform: rotate(125deg);
    background-color: #288DC1;
    border-radius: 20px;
  }

  #toolbarIcon{
    color:#288DC1;
  }

  #image {
    height: 54px;
  }
} 

@media only screen and (min-width: 992px) {
  h1,h2,h3,h4,h5,h6{
    font-size: 36px;
  }

  .content {
    width: 500px;
    padding-left: 25px;
    padding-top: 100px;
  }

  .footer{
    padding-top:200px;
    padding-left:35px;
    width: 150px;
  }

  .box {
    position: absolute;
    height: 90%;
    width: 110%;
    right: -70%;
    top: -50%;
    transform: rotate(125deg);
    background-color: #288DC1;
    border-radius: 20px;
  }

  #toolbarIcon{
    color:#288DC1;
  }

  #image {
    height: 64px;
  }
} 

@media only screen and (max-width: 600px) {
  .content {
    width: 300px;
    padding-left: 15px;
    padding-top: 75px;
  }

  h1,h2,h3,h4,h5,h6{
    font-size: 22px;
  }

  .footer{
    padding-top:120px;
    padding-left:25px;
    width: 150px;
  }

  .navFooter{
    padding-top:390px;
    padding-left:10px;
    width: 135px;
  }

  .box {
    position: absolute;
    height: 90%;
    width: 110%;
    right: -100%;
    top: -35%;
    transform: rotate(125deg);
    background-color: #288DC1;
    border-radius: 20px;
  }

  #toolbarIcon{
    color:white;
  }

  #image {
    height: 48px;
  }
}
</style>
