<template>
  <div class="map-div">
    <l-map
      v-if="showMap"
      style="z-index: 10; width: 100%"
      :zoom="zoom"
      :center="center"
      :options="mapOptions"
      @update:center="centerUpdated"
      @update:zoom="zoomUpdated"
    >
      <l-tile-layer
        :url="url"
        :attribution="attribution"
      ></l-tile-layer>
      <l-marker
        :lat-lng="[lat, lng]"
      >
      </l-marker>
    </l-map>
  </div>
</template>

<script>
import { icon } from "leaflet";
import { LMap, LTileLayer, LMarker } from "vue2-leaflet";

export default {
  props: ['lat', 'lng'],  
  components: {
    LMap,
    LTileLayer,
    LMarker
  },
  data() {
    return {
      url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
      attribution: 
        '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      icon: icon({
        iconUrl: "../images/icon-location.svg",
        iconSize: [32, 37],
        iconAnchor: [16, 37]
      }),
      center: {lat: null, lng: null},
      zoom: 15,
      mapOptions: {
        zoomSnap: 0.5
      },
      showMap: true
    }
  },
  methods: {
    zoomUpdated (zoom) {
      this.zoom = zoom;
    },
    centerUpdated (center) {
      this.center = center;
    }
  },
  watch: {
    lat(val) {
      this.center.lat = val;
    },
    lng(val) {
      this.center.lng = val;
    }
  }
}
</script>

<style scoped>
.map-div {
  height: calc(100vh - 22rem);
  width: 100%;
}
</style>