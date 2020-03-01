<template>
  <div id="app">
    <h1>The International Space Station</h1>
    <h2>{{issPosition.latitude}}</h2>
    <!-- <h1>{{this.astros[0].name}}</h1> -->
    <issTracker :issPosition="issPosition"></issTracker>
    <astrosList :astros="astros"></astrosList>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
import IssMapTracker from './components/IssMapTracker.vue'
import AstrosInSpace from './components/AstrosInSpace.vue'
import {latling} from "leaflet";
import { Lmap, LTileLayer, LMarker} from 'vue2-leaflet'

export default {
  name: 'App',
  data(){
    return{
      issData: {},
      issPosition: {},
      astros: [],
      issPass: {}
    }
  },
  components: {
    'issTracker': IssMapTracker,
    'astrosList': AstrosInSpace
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
