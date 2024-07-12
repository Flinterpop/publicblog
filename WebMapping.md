### Web Mercator

From: https://www.esri.com/arcgis-blog/products/arcgis-pro/mapping/mercator-its-not-hip-to-be-square/

Web Mercator became the default web map tiling scheme for good reason – it was relatively simple to build a seamless, zoomable web map. Conformality meant that shapes were maintained and distortion was relatively low at large scales when zoomed in. 

The reason Web Mercator was suitable as the basis for early web mapping is that it creates a convenient square shape for the entire world if it is truncated at approximately 85° North and South of the Equator. Wherever you are on the map, up is due north, down is due south and west and east are always left and right. At large scales, conformality means square buildings remain square. This creates an attractive consistency from a software engineering perspective and avoids some of the confusion that sometimes comes with other projections.

So, Web Mercator is quite serviceable, particularly for large scale maps, or for regional mapping. But for small scale maps it is virtually useless. For instance, on a world map, Ellesmere Island in the Canadian arctic is shown approximately the same size as Australia. It isn’t. It’s 75,767 mi² in size and has a population of 146. Australia is 2.97 million mi² and has a population of 24.6 million.

Canada is a cartographer’s nightmare. It has a huge landmass that extends across a large north-south extent which sits squarely in the Web Mercator zone of highest distortion. It also has vastly differing population densities across its area from a more densely populated south to an increasingly sparse population in the north. Nearly 90% of the Canadian population live within 100 miles of the border with the United States.



from: https://www.researchgate.net/publication/321064657_Web_mercator_and_raster_tile_maps_two_cornerstones_of_online_map_service_providers

A map projection is a set of functions f that convert the geographic coordinates (latitude or φ, longitude or λ) into Cartesian coordinates (X or Eastings, Y or Northings) onto a two-dimensional plane surface (Figure 2).

<img src="C:\Users\Brad\Dropbox\09_Apps\VSCode\RunningNotes\Fig2Map.png" alt="Fig2Map" style="zoom:50%;" />



The projection adopted for all tiles is Web Mercator with WGS’84 datum.

Google Maps conventions for the aforementioned parameters are as follows. All map tiles are square-shaped and equal sized, i.e., 256x256 pixels. The world is rendered in a single tile at the outer most zoom level and numbered as 0. As explained in Section 3, this layout depicts the earth on the Web Mercator projection (Figure 8) and excludes polar areas. The projection adopted for all tiles is Web Mercator with WGS’84 datum. Each tile at any zoom level k is replaced by 4 equal-sized tiles at zoom level k+1. As the size of each new tile is still 256x256 pixels, the pixel size at level k+1 is four times smaller than the pixel size at level k. The number of tiles at zoom level k is equal to 4^k, e.g., at zoom levels 3 and 17, there are 64 and 17,179,869,184 tiles, while the ground resolution is approx. 20km and 120cm per pixel, respectively (Figure 11).

<img src="C:\Users\Brad\Dropbox\09_Apps\VSCode\RunningNotes\TileTable.png" alt="TileTable" style="zoom:50%;" />



from: https://learn.microsoft.com/en-us/bingmaps/articles/bing-maps-tile-system?redirectedfrom=MSDN



Although the Mercator projection significantly distorts scale and area (particularly near the poles), it has two important properties that outweigh the scale distortion:

1. It’s a **conformal** projection, which means that it preserves the shape of relatively small objects. This is especially important when showing aerial imagery, because we want to avoid distorting the shape of buildings. Square buildings should appear square, not rectangular.
2. It’s a **cylindrical** projection, which means that north and south are always straight up and down, and west and east are always straight left and right.

Since the Mercator projection goes to infinity at the poles, it doesn’t actually show the entire world. Using a square aspect ratio for the map, the maximum latitude shown is approximately 85.05 degrees.



Aside: https://jimmyutterstrom.com/blog/2019/06/05/map-tiles-to-geotiff/

which refs this: https://github.com/jimutt/tiles-to-tiff

Generate merged GeoTIFF imagery from web maps (xyz tile servers) with Python





