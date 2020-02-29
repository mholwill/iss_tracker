<template>
  <div id="app">
    <h1>The International Space Station</h1>
    <h2>{{issPoisition.latitude}}</h2>
    <h1>{{this.astros[0].name}}</h1>
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return{
      issData: {},
      issPoisition: {},
      astros: []
    }
  },
  components: {

  },
  mounted(){
    fetch('http://api.open-notify.org/iss-now.json')
    .then(res => res.json())
    .then((issData) => {
      this.issData = issData
      this.issPoisition = issData.iss_position});

    fetch('http://api.open-notify.org/astros.json')
    .then(res => res.json())
    .then(astros => this.astros = astros.people)
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
