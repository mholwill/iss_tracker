<template>
  <div id="map">
    <h1>{{this.issPosition.latitude}}</h1>
    <l-map
      v-if="showMap"
      :zoom="zoom"
      :center="center"
      :options="mapOptions"
      style="height: 80%"
      >
      <l-tile-layer
      :url="url"
      :attribution="attribution"
      />
    </l-map>
  </div>
</template>
<script>
  import { latLng } from "leaflet";
  import { LMap, LTileLayer, LMarker } from 'vue2-leaflet';
  export default {
    name: 'App',
    components: {
      LMap,
      LTileLayer,
      LMarker
    },
    props: ['issPosition'],
    data() {
      return {
        zoom: 10,
        center: latLng(this.issPosition.latitude, this.issPosition.longitude),
        url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
        attribution:
        '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
        currentZoom: 10,
        center: latLng(this.issPosition.latitude, this.issPosition.longitude),
        showParagraph: false,
        mapOptions: {
          zoomSnap: 0.5
        },
        showMap: true
      }
    }
  }
</script>
<style>
  #yeah-baby{
    height: 300px;
  }
  #map {
    height: 500px;
    width: 75%
  }
</style>
