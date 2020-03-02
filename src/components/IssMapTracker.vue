<template>
<div class="box-container">
  <div id="map">
    <l-map
      v-if="showMap"
      :zoom="zoom"
      :center="center"
      :options="mapOptions"
      :setTimeout="setTimeout"
      style="height: 100%"
      >
      <l-tile-layer
      :url="url"
      :attribution="attribution"
      />
      <l-marker :lat-lng="marker"/>
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
        zoom: 5,
        center: latLng(55.953251, -3.188267),
        url: 'https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}',
        attribution:
        'Tiles &copy; Esri &mdash; Source: Esri, i-cubed, USDA, USGS, AEX, GeoEye, Getmapping, Aerogrid, IGN, IGP, UPR-EGP, and the GIS User Community',
        currentZoom: 2,
        center: latLng(55.953251, -3.188267),
        showParagraph: false,
        marker: L.latLng(55.953251, -3.188267),
        myIcon: L.icon({
          iconUrl: '../../public/images/ISS_Icon.png',
          iconSize: [38, 95],
          iconAnchor: [22, 94],
          popupAnchor: [-3, -76],
        }),
        markerOptions: {

        },
        mapOptions: {
          zoomSnap: 0.5
        },
        showMap: true,
        setTimeout: 5000
      }
    },
    computed: {

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
