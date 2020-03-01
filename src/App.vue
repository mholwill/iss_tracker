<template>
  <div id="app">
    <h1>The International Space Station</h1>
    <h2>{{issPosition.latitude}}</h2>
    <!-- <h1>{{this.astros[0].name}}</h1> -->
    <issTracker :issPosition="issPosition"></issTracker>
    <astrosList :astros="astros"></astrosList>
    <astroDetails :astro="selectedAstro"></astroDetails>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";

import IssMapTracker from './components/IssMapTracker.vue'
import AstrosInSpace from './components/AstrosInSpace.vue'
import AstroDetails from './components/AstroDetails.vue'

import {latling} from "leaflet";
import { Lmap, LTileLayer, LMarker} from 'vue2-leaflet'

export default {
  name: 'App',
  data(){
    return{
      issData: {},
      issPosition: {},
      astros: [],
      issPass: {},
      selectedAstro: null
    }
  },
  components: {
    'issTracker': IssMapTracker,
    'astrosList': AstrosInSpace,
    'astroDetails': AstroDetails
  },
  mounted(){
    fetch('http://api.open-notify.org/iss-now.json')
    .then(res => res.json())
    .then((issData) => {
      this.issData = issData
      this.issPosition = issData.iss_position});

    fetch('http://api.open-notify.org/astros.json')
    .then(res => res.json())
    .then(astrosData => this.astros = astrosData.people)

    eventBus.$on('astro-selected', (astro) => { //NEW
     this.selectedAstro = astro;
    })
  }
}
</script>

<style>
#app {
  font-family: Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 60px;
}
</style>
