---
title: "Welcome to GeoSpatialyst!"
permalink: /homepage/
layout: splash
header:
  overlay_image: "image/Home_page/Home_background.JPG"
  # overlay_filter: radial-gradient(at top left, rgb(255,255,255, 0.5), rgb(0,128,0, 0.5))
intro_1: 
  - excerpt: '"**GeoSpatialyst**, also known as Geospatial Analyst, is a personal and online platform for learning geospatial data science and analysis. Currently, I am providing online training programs for engineering students and engineers who are interested in learning how to solve different GIS-related tasks or geospatial problems in both applications and programming languages."'
intro_2: 
  - excerpt: 'The problems includes creating, storing, manipulating, analyzing, and visualizing (mapping) spatial and temporal information. GeoSpatialyst offers several basic lessons on how to do those tasks with Python programing language and with specific topics. The aim of each topic focuses on dealing with common GIS-related problems which we often face in research and work. Each lesson uses only publicly available data which can be downloaded freely.'
intro_3: 
  - excerpt: 'After learning these lessons, you will be able to instantly start programming and trying out solving different problems with your own materials. Especially, with the basic knowledge you gain from our training, your understanding in using programming platform to work with geospatial data will be greatly improved, and this basics will be essential when you master your skills in GIS data science or solve more complex issues in geospatial analysis.'

feature_row1:
  - image_path: /image/Home_page/map_projection.png
    alt: "map_projection"
    title: "1. An understanding about CRS (Coordinate Reference System)"
    excerpt: 'You will know how to programmatically select an appropriate CRS or projection for your map or modify different kinds of map projection.'

feature_row2:
  - image_path: /image/Home_page/nearest_network.png
    alt: "nearest_network"
    title: "2. Analytical skill with geometric data"
    excerpt: 'You will have more ideas on how to analyze nearest network, nearest area, statistics, patterns or shapes.'

# feature_row3:
#   - image_path: /image/Home_page/open_street_map.jpg
#     alt: "open_street_map"
#     title: "3. Techniques to retreive data from OpenStreetMap"
#     excerpt: 'You will be able to extract or download spatial data from OpenStreetMap such as location of restaurant, park, school, building footprint, road network, etc.'

iframe_1:
  - iframe_url: "https://handsondataviz.github.io/leaflet-heatmap/"
    alt: "interactive_map"
    title_iframe: "3. Ability to create your own static or interactive map"
    excerpt_iframe: 'You can also create both static and interactive map for personal websites or share analyzed data to your friends.'
    url_iframe: "https://handsondataviz.github.io/leaflet-heatmap/"
    btn_class: "btn--success btn--small"
    btn_label: "Click here to view full map"

feature_row4:
  - title: "4. Insight into processing various raster operations"
    excerpt: "You will understand the process in analyzing vector and raster data and the mathematical operation on Satellite images (i.e. visualizing satellite images, masking, calculating indices, extracting area, and exporting results.)"
  - image_path: /image/Home_page/visualize_raster.jpg
    excerpt: "Read and visualize raster file. Check Landsat 8 band combinations [here](https://gsp.humboldt.edu/OLM/Courses/GSP_216_Online/lesson3-1/composites.html) "
  - image_path: /image/Home_page/clipped_area.jpg
    excerpt: "Clip or mask raster image."
  - image_path: /image/Home_page/mosaic.jpg
    excerpt: "Create a mosaic of multiple raster files."
  - image_path: /image/Home_page/indices_and_area.jpg
    excerpt: "Calculate various normalized indices and extract vegetation and water area."
  - image_path: /image/Home_page/exported_img.png
    excerpt: "Save or export results in raster format, and open it in QGIS"

feature_row5:
  - url: "/course/"
    btn_label: "Read More "
    btn_class: "btn--primary btn--primary"
---
{% include feature_row id="intro_1" type="center" %}
{% include feature_row id="intro_2" type="center" %}
{% include feature_row id="intro_3" type="center" %}

## <span style="color:#3fa63f">You'll Walk Away With:</span>
{: style="text-align: center;"}

{% include feature_row id="feature_row1" type="left" %}
{% include feature_row id="feature_row2" type="left" %}
<!-- {% include feature_row id="feature_row3" type="left" %} -->
{% include iframe id="iframe_1" type="left" %}
{% include feature_row id="feature_row4" %}


---
<span style="color:#3fa63f">For more information and details about the course overview, please click 'Read More' button below.</span>
{: style="text-align: center;"}
{% include feature_row id="feature_row5" type="center" %}
{: style="text-align: center;"}
