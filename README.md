

# vue2-leaflet-polylineoffset

This is a [Polyline Offset plugin](https://github.com/bbecquet/Leaflet.PolylineOffset) extension for [vue2-leaflet package](https://github.com/KoRiGaN/Vue2Leaflet).

## Install

    npm install --save vue2-leaflet-polylineoffset

## Demo

    git clone https://github.com/maratumba/vue2-leaflet-polylineoffset

    # using npm
    npm install
    npm run example

Then you should be able to navigate with your browser and see the demo in http://localhost:4000/

You can see the demo code in the file [example.vue](example.vue)

## Usage

### on &lt;template&gt; add

```html
<l-polyline-offset :lat-lngs="latlngs" :offset="offset" />
```

### on &lt;script&gt; add

#### option 1

In the same template file, at `<script>` part, this will make the component available only to the template in this file

```js
import LPolylineOffset from 'vue2-leaflet-polylineoffset'
...
export default {
    ...
    components: {
    LPolylineOffset,
    ...
    },
    ...
}
```

#### option 2

At main Vue configuration, this will make the component available to all templates in your app

```js
import Vue from 'vue'
import LPolylineOffset from 'vue2-leaflet-polylineoffset'
...
Vue.component('l-polyline-offset', LPolylineOffset)
```

## Develop and build
```sh
npm install
npm run build
```
## Author

[maratumba](https://github.com/maratumba/)


## License

MIT
polyline offset plugin extension for vue2-leaflet package
