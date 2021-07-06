---
classes: wide
title: "Session 1"
permalink: /course/session-1/
layout: single
sidebar:
  nav: "docs"
toc: true
img_1:
  - image_path: /geospatial_course/img/session_1/shapely_classes.png
feature_row1:
  - image_path: /geospatial_course/img/session_1/shapely_classes.png
---

# Session 1: Geometric Objects

## 1. General overview

In this session, we will learn the most fundamental geometric objects (i.e. Points, Lines and Polygons) which are important vector elements in spatial data analysis. In order to read or write these objects in Python, we use a package called [Shapely](https://shapely.readthedocs.io/en/stable/manual.html). Shapely is a Python package for the manipulation and analysis of two-dimensional geospatial geometries. Without further delay, we will do different kinds of geometric operations with Shapely module as following:
{: style="text-align: justify;"}

* Create a `Line` or `Polygon` from a collection of `Point` geometries
* Calculate areas/length/bounds etc. of input geometries
* Conduct geometric operations based on the input geometries such as `Union`, `Difference`, `Distance` etc.
* Conduct spatial queries between geometries such as `Intersects`, `Touches`, `Crosses`, `Within` etc.

#### Major classes in Shapely  

Shapely itself consists of eight major classes, representing different types of geometrical shapes:
* The `Point` class represents a single point in space. Points can be two- dimensional (x, y), or three-dimensional (x, y, z).
* The `LineString` class represents a sequence of points joined together to form a line. LineStrings can be simple (no crossing line segments) or complex (where two line segments within the LineString cross).
* The `LinearRing` class represents a line string which finishes at the starting point. The line segments within a LinearRing cannot cross or touch.
* The `Polygon` class represents a filled area, optionally with one or more "holes" inside it.
* The `MultiPoint` class represents a collection of Points.
* The `MultiLineString` class represents a collection of LineStrings.
* The `MultiLineString` class represents a collection of LineStrings.
* The `MultiPolygon` class represents a collection of Polygons.
* The `GeometryCollection` class represents a collection of any combination of Points, LineStrings, LinearRings, and Polygons.

{% include feature_row id="feature_row1" type="center" %}

## 2. Geometric Objects
Let's learn how to create Point, Line and Polygon with Shapely module by passing coordinates (x, y [, z]) into `Point()`, `LineString()`, and `Polygon()`

**Problems**: We have 4 points (i.e. Point 1: (0, 0); Point 2: (1, 1); Point 3: (2, 2); and Point 4: (3, 3)). Let's create Point, Line and Polygon from given points' coordinates.

```python
In[1]:

# Import Shapely module
from shapely.geometry import Point, LineString, Polygon

point1 = Point(2.2, 4.2)
point2 = Point(7.2, -25.1)
point3 = Point(9.26, -2.456)
point4 = Point(7.2, -2.456)
point3D = Point(9.26, -2.456, 0.57)
```
Now we can see how each point looks like:

```python
In[2]:

point1
```

{::options parse_block_html="true" /}

<details><summary markdown="span"></summary>
![svg](/site/geospatial_course/img/session_1/output_4_0.svg)
</details>
<br/>

{::options parse_block_html="false" /}


To check the information of each point, we use the `Print()` statement as follows:

```python
In[3]:

print(point1)
print(point3D)
```

{::options parse_block_html="true" /}
<details><summary markdown="span"></summary>
```
POINT (2.2 4.2)
POINT Z (9.26 -2.456 0.57)
```
</details>
<br/>
{::options parse_block_html="false" /}


When passing 3-dimension point, it will result in letter `Z` in front of object definition. 

So let's check the type of a point


```python
type(point1)
```




    shapely.geometry.point.Point



We can also check the geometry type of the object by using `Point.geom_type`:


```python
point1.geom_type
```




    'Point'



So far you know how to create Point and check its geometric information. Now, let's create LingString by using `LineString()` statement as follows:


```python
line = LineString([(0, 0), (1, 1)])
line
```




![svg](output_13_0.svg)



Now, we use the points we created to make linestring with more than 2 points.


```python
line = LineString([point1,  point2, point3])
line
```




![svg](output_15_0.svg)




```python
line.bounds
```




    (2.2, -25.1, 9.26, 4.2)




```python

```


```python

```
