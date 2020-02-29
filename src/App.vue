<template>
  <div id="app">
    <h1>The International Space Station</h1>
    <h2>{{issPosition.latitude}}</h2>
    <!-- <h1>{{this.astros[0].name}}</h1> -->
    <issTracker :issPosition="issPosition"></issTracker>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
import IssMapTracker from './components/IssMapTracker.vue'

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
    'issTracker': IssMapTracker
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

    // fetch('http://api.open-notify.org/iss-pass.json?lat=55.947145&lon=-3.202079&alt=20&n=5')
    // .then(res => res.json())
    // .then(issPassData => this.issPass = issPassData)
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
