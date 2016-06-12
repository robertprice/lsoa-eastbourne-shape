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
