# Leaflet.hotline

A Leaflet plugin for drawing colored gradients along polylines. This is useful for visualising values along a course, for example: elevation, velocity, or heart rate.  
Inspired by [Leaflet.heat](https://github.com/Leaflet/Leaflet.heat/).


## Requirements

Leaflet.hotline only works with **Leaflet 1.0-dev**. You can [download](http://leaflet-cdn.s3.amazonaws.com/build/leaflet-master.zip) it or build it from [source](https://github.com/Leaflet/Leaflet) (use the master branch). It creates its own renderer that draws on a canvas element.


## Installation

* Run `npm install leaflet.hotline`
* or download the latest package


## Demo

<https://iosphere.github.io/Leaflet.hotline/demo/>


## Basic usage

### Node.js / Browserify

```js
// Include Leaflet
var L = require('leaflet')

// Pass Leaflet to the plugin.
// Only required to overload once, subsequent overloads will return the same instance.
require('leaflet.hotline')(L);

// Create a hotline layer
var hotlineLayer = L.hotline(data, options).addTo(map);
```

### Browser

```html
<!-- Include Leaflet -->
<script src="path/to/leaflet.js"></script>
<!-- Include Leaflet.hotline -->
<script src="path/to/leaflet.hotline.js"></script>
<script>
	// Create a hotline layer
	var hotlineLayer = L.hotline(data, options).addTo(map);
</script>
```


## Documentation

`L.Hotline` extends [`L.Polyline`](http://leafletjs.com/reference.html#polyline). You can use all its methods and most of its options, except the ones for styling.

```js
// Create a hotline layer via the factory...
var hotlineLayer = L.hotline(data, options).addTo(map);

// ... or via the constructor
var hotlineLayer = new L.Hotline(data, options).addTo(map);
```

### `data`

The `data` parameter needs to be an array of `LatLng` points (a polyline) with an additional third element in each point, like the elevation, that determines which color from the `palette` to use. Multiple polylines are supported.

### `options`

You can use the following options to style the hotline:

- **weight** - Same as usual. `5` per default.
- **outlineWidth** - The width of the outline along the stroke in pixels. Can be `0`. `1` per default.
- **outlineColor** - The color of the outline. `'black'` per default.
- **palette** - The config for the palette gradient in the form of `{ <stop>: '<color>' }`. `{ 0.0: 'green', 0.5: 'yellow', 1.0: 'red' }` per default. Stop values should be between `0` and `1`.
- **min** - The smallest z value expected in the `data` array. This maps to the `0` stop value. Any z values smaller than this will be considered as `min` when choosing the color to use.
- **max** - The largest z value expected in the `data` array. This maps to the `1` stop value. Any z values greater than this will be considered as `max` when choosing the color to use.


## Building

`npm install && npm run build`


## Credits

* [@mourner](https://github.com/mourner) for [Leaflet](https://github.com/Leaflet/Leaflet/) and [Leaflet.heat](https://github.com/Leaflet/Leaflet.heat/)
* [@orrc](https://github.com/orrc) for the name