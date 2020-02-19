<template>
  <div>
      <l-map
      :center="[40.836566,29.514314]"
      style="height: 400px; width: 100%"
      :zoom="12"
      >
        <l-tile-layer ref="layerRef" :options="{maxNativeZoom:18,maxZoom:24}" :url="url"></l-tile-layer>
        <l-polyline-offset 
          :lat-lngs="[[40.836566,29.514314],[40.846566,29.524314]]"
          :offset="5"
        />
        <l-polyline
          :lat-lngs="[[40.836566,29.514314],[40.846566,29.524314]]"
        />
    </l-map>
  </div>
</template>

<script>
import LPolylineOffset  from 'Vue2LeafletPolylineOffset';
import { LMap, LTileLayer, LPolyline } from 'vue2-leaflet';
import { Icon } from 'leaflet';

import 'leaflet/dist/leaflet.css';

// this part resolve an issue where the markers would not appear
delete Icon.Default.prototype._getIconUrl;

export default {
  name: 'poly-offset-test',
  components: {
    LMap,
    LPolylineOffset,
    LTileLayer,
    LPolyline,
  },
  data: function(){ return{
    url: 'https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}',
  }},
}
</script>

<style>

</style>