<template>
  <div style="display: none;">
    <slot v-if="ready" />
  </div>
</template>
<script>

import { optionsMerger, propsBinder, findRealParent } from 'vue2-leaflet/dist/utils/utils.js';
import PolylineMixin from 'vue2-leaflet/dist/mixins/Polyline.js';
import Options from 'vue2-leaflet/dist/mixins/Options.js';
import { polyline, DomEvent } from 'leaflet';
import 'leaflet-polylineoffset';

export default {
  name: 'LPolylineOffset',
  mixins: [PolylineMixin, Options],
  props: {
    latLngs: {
      type: Array,
      default: () => [],
    },
    offset: {
      type: Number,
      default: () => 0,
    }
  },
  data() {
    return {
      ready: false,
    };
  },
  watch: {
    offset: function(val){
      if(this.mapObject) this.mapObject.setOffset(val);
    }
  },
  mounted() {
    const options = optionsMerger(this.polyLineOptions, this);
    this.mapObject = polyline(this.latLngs, options);
    DomEvent.on(this.mapObject, this.$listeners);
    propsBinder(this, this.mapObject, this.$options.props);
    this.ready = true;
    this.parentContainer = findRealParent(this.$parent);
    this.parentContainer.addLayer(this, !this.visible);
    this.mapObject.setOffset(this.offset);
    console.log(this)
    this.$nextTick(() => {
      /**
       * Triggers when the component is ready
       * @type {object}
       * @property {object} mapObject - reference to leaflet map object
       */
      this.$emit('ready', this.mapObject);
    });
  },
};
</script>
