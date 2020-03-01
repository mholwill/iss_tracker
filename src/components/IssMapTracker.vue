<template>
<div class="box-container">
  <div id="map">
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
      <!-- <l-marker :lat-lng="markers"/> -->
    </l-map>
  </div>
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
        zoom: 2,
        center: latLng(55.9533456, -3.1883749),
        url: 'https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}',
        attribution:
        'Tiles &copy; Esri &mdash; Source: Esri, i-cubed, USDA, USGS, AEX, GeoEye, Getmapping, Aerogrid, IGN, IGP, UPR-EGP, and the GIS User Community',
        currentZoom: 2,
        center: latLng(55.9533456, -3.1883749),
        showParagraph: false,
        // markers: [
        //   L.latLng(55.9533456, -3.1883749)
        // ],
        mapOptions: {
          zoomSnap: 0.5
        },
        showMap: true
      }
    }
  }
</script>
<style>

  .box-container {
    display: flex;
    justify-content: center;
  }

  #map {
    height: 500px;
    width: 75%;
    margin: 0;
    padding: 0;
  }

  l-map {
    height: auto;
  }
</style>
