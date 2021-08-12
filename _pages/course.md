---
title: "Geospatial Data Analysis with Python"
permalink: /course/
layout: splash
author_profile: false
header:
  overlay_image: "/image/Course_page/computer_python.jpg"
  # overlay_filter: radial-gradient(at top left, rgb(255,255,255, 0.5), rgb(0,128,0, 0.5))
  # linear-gradient(0.25turn, rgba(255, 0, 0, 0.5), rgba(0, 255, 255, 0.5))
  # actions:
  # - label: "<i class='btn--primary'></i> Course Details"
  #   url: "/course/class-overview/" 
# tagline: "Master your ability in spatial data analysis."
poster:
  - image_path: /image/Course_page/poster.jpg

feature_row1:
  # - url: "https://forms.gle/tvYPyhrPKpGGrLc56"
    btn_label: "Register is Closed"
    btn_class: "btn--success btn--primary"


---
### Course Introduction
<span style="color:#3fa63f">**Geospatial Data Analysis with Python**</span>
 is an online training course provided by GeoSpatialyst to teach you how to programmatically analyze geospatial data with Python. The course consists of six interactive sessions starting from learning general operations on geometric features to analyzing satellite images (i.e. reading and writing raster formats). In this course, students will mostly sit in front of computer since they will learn to program and do pratical exercises in Python language alongside with the course convener. We will focus on applying programming skills to do various tasks without using any tool in GIS but producing the same or better result and faster than GIS.
 {: style="text-align: left;"}

<!-- ![image-left]({{ site.url }}{{ site.baseurl }}/image/Course_page/poster.jpg){: .align-left} The rest of this paragraph is filler for the sake of seeing the text wrap around the 150×150 image, which is **left aligned**. -->

<!-- <figure style="width: 300px" class="align-left">
  <img src="{{ site.url }}{{ site.baseurl }}/image/Course_page/poster.jpg" alt="">
</figure>  -->



### Course Requirement
{: style="text-align: left;"}
To gain the most from the course, it's necessary to know the basics of ArcGIS or QGIS and Python programming. You don't need to be very good at it, but at least you should know the main files in GIS such as vector or raster files and have little experience in Python. If you are new to Python, you might find it a bit difficult to follow the lessons, but it doesn't mean you can't take this course because you'll never know until you try.
{: style="text-align: left;"}

### Course Environment
{: style="text-align: left;"}
In this online course, we will use [JupyterLab](https://jupyterlab.readthedocs.io/en/stable/getting_started/overview.html), a web-based user interface, as the main programming environment. It enables you to work with documents and activities such as Jupyter notebooks (`.ipynb`-files), text editors, terminals, and custom components in a flexible, integrated, and extensible manner. All of the code materials in this course are in `.ipynb`-files which you can run in JupyterLab on your own computer.
{: style="text-align: left;"}

### Course Schedule
{: style="text-align: left;"}

| Week     | Date          | Day        | Time (in Cambodia) | Duration        | Session topics                                          |
|:--------:|:-------------:|:----------:|-------------------:|----------------:|---------------------------------------------------------|
| Week 1   | 24/Jul/2021   | Saturday   | 10:00AM ~ 11:30AM  | 1h ~ 1h30       | 1. Introduction to Python and Geometric objects         |
|          | 25/Jul/2021   | Sunday     | 10:00AM ~ 11:30AM  | 1h ~ 1h30       | 2. Vector data analysis and map projection              |
| Week 2   | 31/Jul/2021   | Saturday   | 10:00AM ~ 11:30AM  | 1h ~ 1h30       | 3. Geocoding and nearest neighbour analysis             |
|          | 01/Aug/2021   | Sunday     | 10:00AM ~ 11:30AM  | 1h ~ 1h30       | 4. Geometric operation and data classification          |
| Week 3   | 07/Aug/2021   | Saturday   | 10:00AM ~ 11:30AM  | 1h ~ 1h30       | 5. Plotting static and interactive map on Leaflet       |
|          | 08/Aug/2021   | Sunday     | 10:00AM ~ 11:30AM  | 1h ~ 1h30       | 6. Satellite image analysis                             |


 <font size="2">Notice: The time to study might be changed to fit with everyone's schedule.</font> 
{: style="text-align: left;"}


### Registration and Cost
{: style="text-align: left;"}
The course is now open for registration, and for those who are interested in this course can register through Google form below:
{: style="text-align: left;"}
* Register: <span style="color:#CB4335">Closed</span>
* Registration deadline: <span style="color:#CB4335">23rd July 2021</span>
{: style="text-align: left;"}

The cost to participate in this course is 40 USD, and you will be contacted about payment after you register.
{: style="text-align: left;"}

### Course Objectives
{: style="text-align: left;"}
In this course, you will learn from the basic level of using Python for geospatial data analysis to advanced level of analyzing the satellite image retrieved from dataset in [Google Earth Engine](https://earthengine.google.com). In each session, you are supposed to gain the following knowledge:
{: style="text-align: left;"}
**<span style="color:#CB4335">Session 1: Introduction to Python and Geometric objects</span>**
{: style="text-align: left;"}
- Understand the web-based JupyterLab for Python
- Know the Python module for geometric objects
- Know how to create different kind of geometries (i.e Point, LineString, Polygon, geometric collections, etc)
- Know how to use different functions to do basic calculation on geometric objects (i.e calculate area, length, perimeter, centroid, etc) 
{: style="text-align: left;"}
**<span style="color:#CB4335">Session 2: Vector data analysis and map projection</span>**
{: style="text-align: left;"}
- Know the Python module for geospatial data
- Read and write vector files (shp, geojson, kml..)
- Plot vector data
- Create geometries into GeoDataFrame
- Analyze attribute data
- Set and change the coordinate reference system of data
{: style="text-align: left;"}
**<span style="color:#CB4335">Session 3: Geocoding and nearest neighbour analysis</span>**
{: style="text-align: left;"}
- Understand about geocoding
- Convert location names to coordinates
- Geocode a set of addresses to coordinate data from OpenStreetMap
- Plot those addresses location in a map
- Conduct spatial queries. Ex: finding points in polygon
- Find the nearest locations or points between two sets of data
{: style="text-align: left;"}
**<span style="color:#CB4335">Session 4: Geometric operation and data classification</span>**
{: style="text-align: left;"}
- Conduct overlay analysis such as clipping or intersection, union, difference, etc
- Conduct a loop operation of overlay analysis
- Aggregate the geometries
- Classify data features based on standard classification methods
- Create custom classifier for data feature classification
{: style="text-align: left;"}
**<span style="color:#CB4335">Session 5: Plotting static and interactive map on Leaflet</span>**
{: style="text-align: left;"}
- Create and customize static map with different background basemap 
- Create and customize interactive map
- Get to know GitHub repository
- Share and publish interactive map on GitHub page
{: style="text-align: left;"}
**<span style="color:#CB4335">Session 6: Satellite image analysis</span>**
{: style="text-align: left;"}
- Understand the Python modules for raster data 
- Read and write satellite or raster image
- Understand about image properties and bands
- Plot raster data and visualize different color composites
- Conduct geometric operation on raster data (i.e masking/clipping, mosaic/merge, etc)
- Calculate various index of raster data (i.e vegetation indice (NDVI), water indice (NDWI), etc)
- Sample raster data using points
- Extract cross-section shape from Digital Elevation Model
{: style="text-align: left;"}

{% include feature_row id="feature_row1" type="center" %}

### Poster
{% include style="width: 300px" feature_row id="poster" type="left" %}