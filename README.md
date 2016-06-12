# lsoa-eastbourne-shape
Shape files for Eastbourne [LSOA](http://webarchive.nationalarchives.gov.uk/20160105160709/http://www.ons.gov.uk/ons/guide-method/geography/beginner-s-guide/census/super-output-areas--soas-/index.html) (Lower Super Output Areas)

## Plotting in R

The LSOA map can be drawn in R using the following.

```r
setwd('/path/to/lsoa-eastbourne-shape')
library(rgdal)
lsoa <- readOGR(".", "eastbourne_lsoa", verbose = FALSE)
plot(lsoa, border = "black")
```

The LSOA map can be drawn in R and overlaid on a Google Map using the following code.

```r
setwd('/path/to/lsoa-eastbourne-shape')

library(rgdal)
library(ggmap)
library(ggplot2)
library(maptools)

lsoa <- readOGR(".", "eastbourne_lsoa", verbose = FALSE)
lsoa <- spTransform(lsoa, CRS("+init=epsg:4326"))
lsoa.f <- fortify(lsoa, region="LSOA11CD")
bb <- as.vector(lsoa@bbox)
map <- get_map(location = bb, maptype = "roadmap", color = "bw", zoom = 12)
ggmap(map, extent = "device") + geom_polygon(data = lsoa.f, aes(long,lat, group=group), colour = "black", size = 0.2, fill = NA)
```
