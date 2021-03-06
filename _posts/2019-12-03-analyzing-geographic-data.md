---
layout: post
title: Visualizing and analyzing geographic data
---

This post is written as a follow-up to my post on [JavaScript mapping](https://ptvan.github.io/javascript-interactive-streetmap/). In the early 2000's I worked in ecology as a GIS modeler and (very briefly) [in the field](https://www.fs.usda.gov/colville/). Back then ArcView dominated GIS, especially in government agencies. In 2019 ArcView is called [ArcGIS](https://www.esri.com/en-us/arcgis/products/arcgis-pro/overview), and still looks to be dominant, though alternatives like the open-source [qGIS](https://www.qgis.org) and the commercial [eSpatial](https://www.espatial.com/mapping-software) have matured. Also now you can do many GIS tasks like geocoding and spatial querying without having a full-blown GIS. You just need R and its friendly neighborhood packages.

### Scale matters

Before you install every R geographic package in CRAN or GitHub, it's important to know the physical scale of the task your're performing. Mapping at street level is different when mapping countries or entire regions. For one, you don't need to worry about projection in the former but they are critically important in the latter. So a static map of the continental US only needs a [single function call](https://github.com/ptvan/R-snippets/blob/master/geographic_analysis.R). Similarly, if you want to highlight a few cities on that map, simply adding the corresponding markers directly via their latitude+longitude will work, without needing the overkill of a full-blown geocoding workflow.

### The R ecosystem for working with geographic data

For obtaining data, the `rnaturalearth` package draws from the excellent [database of the same name](http://www.naturalearthdata.com/), similarly `osmdata` pulls from [OpenStreetMap](https://www.openstreetmap.org).

For data structures, one well-known package is `sf`, which allows you to store **S**imple **F**eatures. Geographic data are for the most part tabular, so you can do all the wrangling using `tidyverse` tools if you wish. To calculate spatial auto-correlation (eg. [Moran's I](https://en.wikipedia.org/wiki/Moran%27s_I)), you can use the `spdep` package.

For handling projections, the low-level `GDAL` library provides bindings for both R (in the form of [rgdal](https://cran.r-project.org/web/packages/rgdal/index.html)) and python.

To detect clusters of objects in geographic data, particularly useful in spatial epidemiology, `SpatialEpi` implements the classic [Besag-Newell](https://www.jstor.org/stable/2982708) algorithm, and `scanstatistics` implements different scan statistics, such as [Kulldorff's](https://www.tandfonline.com/doi/abs/10.1080/03610929708831995).

For plotting maps, `ggplot2` conveniently implements `geom_sf` for static maps, and `coord_sf` for projection, as described in this [great writeup on r-spatial.org](https://www.r-spatial.org/r/2018/10/25/ggplot2-sf.html).

Geocoding requires a bit more work. `ggmap` supports GoogleMaps and OpenStreetMap, which I prefer since it doesn't require an API key. If you want to geocode IP addresses, there is an appropriately named [r_IPgeocode](https://github.com/cengel/r_IPgeocode) package for that, of course.

If instead you want to create [hexbin maps](https://www.data-to-viz.com/graph/hexbinmap.html), _eg._ election results, the `rgeos` package can calculate centroids of each bin, which can then be fortified to a ```geom_polygon```, as demonstrated [here](https://www.r-graph-gallery.com/328-hexbin-map-of-the-usa.html).

### It's good to be polyglot: geographic data in Python

If you're working in Python, [GeoViews](http://geoviews.org/) for handling large-scale maps, part of the [HoloViz](http://holoviz.org)* collection of libraries. For visualization, you can use the old-school [matplotlib](https://matplotlib.org/), the new-school [seaborn](https://seaborn.pydata.org/), as well as a [Python version of ggplot](http://ggplot.yhathq.com/). If you need interactivity, the web-oriented [Bokeh](https://docs.bokeh.org/en/latest) works well.

*_Somewhat confusingly, HoloViz also provides `hvPlot`, which allows general-purpose plotting that partially overlaps with seaborn/matplotlib/ggplot._
