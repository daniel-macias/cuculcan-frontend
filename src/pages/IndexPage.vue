<template>
  <q-page class="page-container">
    <div id="map" class="map"></div>
  </q-page>
</template>

<script setup>
import { onMounted, ref, inject, watch } from "vue";
import axios from "axios";
import Map from "ol/Map";
import View from "ol/View";
import TileLayer from "ol/layer/Tile";
import OSM from "ol/source/OSM";
import VectorLayer from "ol/layer/Vector";
import VectorSource from "ol/source/Vector";
import { GeoJSON } from "ol/format";
import { fromLonLat } from "ol/proj";
import { Style, Stroke } from "ol/style";

const map = ref(null);

defineOptions({
  name: "IndexPage",
});

onMounted(() => {
  map.value = new Map({
    target: "map",
    layers: [
      new TileLayer({
        source: new OSM(),
      }),
    ],
    view: new View({
      center: fromLonLat([-80.0, 15.0]),
      zoom: 6,
    }),
  });
});
</script>

<style scoped>
.page-container {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.map {
  width: 100%;
  height: 100%;
}
</style>
