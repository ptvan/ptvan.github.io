---
layout: post
title: Geographic Data in R
---

This post is written as a follow-up to my post on [JavaScript mapping](https://ptvan.github.io/javascript-interactive-streetmap/). In the early 2000's I worked in ecology as a GIS modeler and (very briefly) [in the field](https://www.fs.usda.gov/colville/). Back then ArcView dominated GIS, especially in government agencies. In 2019 it's called [ArcGIS](https://www.esri.com/en-us/arcgis/products/arcgis-pro/overview), and still looks to be dominant, though alternatives like the open-source [qGIS](https://www.qgis.org) and commercial [eSpatial](https://www.espatial.com/mapping-software) have matured. Also, you can do many GIS tasks like geocoding and spatial querying without having a full-blown GIS. You just need R and its friendly neighborhood packages.

### The R ecosystem for working with geographic data
Probably the most well-known package (at least to me) is `sf`, which allows you to store Simple Features (hence the name abbreviation). Geographic data are for the most part tabular, so you can do all the wrangling using `tidyverse` tools if you wish. 

For the data itself, the `rnaturalearth` package draws from the excellent [database of the same name](http://www.naturalearthdata.com/), similarly `osmdata` pulls from [OpenStreetMap](https://www.openstreetmap.org). For plotting, `ggplot2` conveniently implements `geom_sf` for static maps, and `coord_sf` for projection, as described in this [great writeup on r-spatial.org](https://www.r-spatial.org/r/2018/10/25/ggplot2-sf.html). 

Geocoding requires a bit more work, `ggmap` supports GoogleMaps and OpenStreetMap (which I prefer since it doesn't require an API key). If you want to geocode IP addresses, there is an appropriately name[r_IPgeocode](https://github.com/cengel/r_IPgeocode) package for that, of course.

### Scale matters
Before you install every R geographic package in CRAN (GitHub?), it's important to know the scale you're working at. Mapping at street level is different when mapping countries or entire regions. For one, you don't need to worry about projection in the former but they are critically important in the latter. So a static map of the continental US only needs a [single function call](https://github.com/ptvan/R-snippets/blob/master/geographic_analysis.R). Similarly, if you want to highlight certain cities on that map, just adding the corresponding markers directly via their latitude+longitude is enough, without the overkill of geocoding.

### Horses for courses
Like the [ship of Theseus](https://en.wikipedia.org/wiki/Ship_of_Theseus) you can only change something so far before it no longer feels like itself. You can't call R a real GIS even if it replicates many of the functions. And while using R gives you convenience of `tidyverse` and reproducibility, sometimes it's easier or faster just to point-and-click your way through an answer.
