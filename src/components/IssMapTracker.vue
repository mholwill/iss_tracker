<template lang="html">
  <div class="">
    <h1>Hello</h1>
    <div id="map"></div>
  </div>
</template>

<script>
import L from 'leaflet';

export default {
  name: "Iss-Tracker",
  data(){
    return {
      map: null,
      tileLayer: null,
      layers: []
    }
  },
  props: ['issPosition'],
  mounted() {
    this.initMap();
    this.initLayers();
  },
  methods: {
    initMap() {
      this.map = L.map('map').setView([38.63, -90.23], 12);

      this.tileLayer = L.tileLayer(
        'https://cartodb-basemaps-{s}.global.ssl.fastly.net/rastertiles/voyager/{z}/{x}/{y}.png',
      {
      maxZoom: 18,
      attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>, &copy; <a href="https://carto.com/attribution">CARTO</a>',
      }
      );
      this.tileLayer.addTo(this.map);
    },
  initLayers() {},
},
}

</script>

<style lang="css" scoped>

  #map {
    height: 200px
  }

</style>
