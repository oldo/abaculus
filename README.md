## abaculus
a small block of stone, tile, glass, or other material used in the construction of a mosaic

or, 

a library for creating static maps from tiles based on center or corner lng,lat coordinates.
Uses node-blend to stitch tiles together.

### usage


#### input:

`scale` is an integer between 1-4 and sets resolution (`scale: 1` is 72dpi, `scale: 4`, is 288dpi)

`zoom` denotes zoom level

`x` is a longitude coordinate, `y` is a latitude coordinate

`width` and `height` are the desired pixel bounds for a map with a center coordinate. Will be multiplied by scale to maintain resolution.

`getTile` is a function that returns a tile buffer based on `z`, `x`, `y` arguments, such as from [tilelive-vector](http://github.com/mapbox/tilelive-vector).

```javascript
var params = {
	zoom: {zoom},
	scale: {scale}
    corners: {   
        topLeft: {
            x: {x}, 
            y: {y}
        },
        bottomRight: {
            x: {x}, 
            y: {x}
        }
    },
    format: 'png',
    getTile = {[Function]}
};
```
or 
```javascript
var params = {
	zoom: {zoom},
	scale: {scale}
    center: {   
    	x: {x},
    	y: {y},
    	w: {width},
    	h: {height}
    },
    format: 'png',
    getTile = {[Function]}
};
```
#### usage:
``` javascript
abaculus(params, function(err, image){
       if (err) return err;
       return image;
	});
```

#### output:
an image of desired resolution for the selected area.
