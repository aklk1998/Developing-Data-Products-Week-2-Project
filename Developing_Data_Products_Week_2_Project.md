---
title: "Developing Data Products Week 2 Project"
author: "AK"
date: "May 02, 2018"
output:
  html_document:
    keep_md: yes
---





# Creation of a web page using R Markdown that features a map created with Leaflet.  

## Assignment

The basic goal of this assignment is to create a web page using R Markdown that features a map created with Leaflet and the map must contain the date that you created the document, and it is 2 months before the date that this assignment is graded



```r
suppressPackageStartupMessages(library(dplyr))
suppressPackageStartupMessages(library(leaflet))
```

```
## Warning: package 'leaflet' was built under R version 3.4.4
```

```r
suppressPackageStartupMessages(library(shiny))
```

```
## Warning: package 'shiny' was built under R version 3.4.4
```

```r
suppressPackageStartupMessages(library(miniUI))
```

```
## Warning: package 'miniUI' was built under R version 3.4.4
```

```r
suppressPackageStartupMessages(library(plotly))
```

```
## Warning: package 'plotly' was built under R version 3.4.4
```

```
## Warning: package 'ggplot2' was built under R version 3.4.4
```

```r
suppressPackageStartupMessages(library(tidyr))
```

```
## Warning: package 'tidyr' was built under R version 3.4.4
```

```r
suppressPackageStartupMessages(library(htmltools))
```

```
## Warning: package 'htmltools' was built under R version 3.4.4
```

```r
suppressPackageStartupMessages(library(htmlwidgets))
```

```
## Warning: package 'htmlwidgets' was built under R version 3.4.4
```

```r
suppressPackageStartupMessages(library(lubridate))
```

```
## Warning: package 'lubridate' was built under R version 3.4.4
```

```r
library(dplyr)
library(leaflet)
library(shiny)
library(miniUI)
library(plotly)
library(tidyr) 
library(htmlwidgets)
library(htmltools)
library(htmlwidgets)
library(htmltools)
library(lubridate)
```



```r
Ontario<-c("<a href='https://www.toronto.ca/services-payments/venues-facilities-bookings/booking-city-facilities/civic-centres/city-hall/'>Toronto City Hall</a>","<a href='http://www.ontla.on.ca/web/home.do'>Ontario Legislative Assembly</a>")

Ontariolocation<-data.frame(lat=c(lat=43.653908,43.6644),lng=c(-79.384293,-79.3923))

Ontariolocationlat<-c(lat=43.653908,43.6644)
Ontariolocationlng<-c(lng=-79.384293,-79.3923)

today_date<-Sys.Date()
two_months_ago <- Sys.Date() %m-% months(2)
tag1<-tags$h1("Today Date is: ",today_date,"Creation Date",two_months_ago)

my_map<-Ontariolocation %>% 
leaflet() %>%
addTiles() %>%
addMarkers(popup=Ontario) %>% 
addControl(tag1, position = "bottomleft")
my_map
```

<!--html_preserve--><div id="htmlwidget-3107026b67fdcfb5f2c4" style="width:672px;height:480px;" class="leaflet html-widget"></div>
<script type="application/json" data-for="htmlwidget-3107026b67fdcfb5f2c4">{"x":{"options":{"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}}},"calls":[{"method":"addTiles","args":["//{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",null,null,{"minZoom":0,"maxZoom":18,"tileSize":256,"subdomains":"abc","errorTileUrl":"","tms":false,"noWrap":false,"zoomOffset":0,"zoomReverse":false,"opacity":1,"zIndex":1,"detectRetina":false,"attribution":"&copy; <a href=\"http://openstreetmap.org\">OpenStreetMap<\/a> contributors, <a href=\"http://creativecommons.org/licenses/by-sa/2.0/\">CC-BY-SA<\/a>"}]},{"method":"addMarkers","args":[[43.653908,43.6644],[-79.384293,-79.3923],null,null,null,{"interactive":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},["<a href='https://www.toronto.ca/services-payments/venues-facilities-bookings/booking-city-facilities/civic-centres/city-hall/'>Toronto City Hall<\/a>","<a href='http://www.ontla.on.ca/web/home.do'>Ontario Legislative Assembly<\/a>"],null,null,null,null,{"interactive":false,"permanent":false,"direction":"auto","opacity":1,"offset":[0,0],"textsize":"10px","textOnly":false,"className":"","sticky":true},null]},{"method":"addControl","args":["<h1>\n  Today Date is: \n  2018-05-03\n  Creation Date\n  2018-03-03\n<\/h1>","bottomleft",null,"info legend"]}],"limits":{"lat":[43.653908,43.6644],"lng":[-79.3923,-79.384293]}},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->

```r
saveWidget(my_map, file="Developing_Data_Products_Week_2_Project.html")
```
