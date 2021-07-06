---
title: "Session 2"
permalink: /course/session-2/
layout: single
sidebar:
  nav: "docs"
toc: true
---

```python
import rasterio     # import the main rasterio function
from rasterio.plot import show, show_hist # some specific rasterio functions we'll need

import matplotlib   # matplotlib is the primary python plotting and viz library
import matplotlib.pyplot as plt

# this bit of magic allows matplotlib to plot inline ina  jupyter notebook
%matplotlib inline  
import folium       # folium is an interactive mapping library

# Import the numpy module
import numpy as np

import os
from pyproj import CRS
```


```python
# import data
raster = rasterio.open('20OCT13031506-S2AS-013787851010_01_P001.TIF')
# Read the grid values into numpy arrays
nir = raster.read(4)
red = raster.read(3)
green = raster.read(2)
blue = raster.read(1)

# Function to normalize the grid values
def normalize(array):
    """Normalizes numpy arrays into scale 0.0 - 1.0"""
    array_min, array_max = array.min(), array.max()
    return ((array - array_min)/(array_max - array_min))
# Normalize the bands
nirn = normalize(nir)
redn = normalize(red)
greenn = normalize(green)
bluen = normalize(blue)
```

# 1. Calculate NDVI and Vegetation Extraction

## NDVI Calculation


```python
# Convert to floats
red = red.astype('f4')
nir = nir.astype('f4')

def get_ndvi(nir, red):
    # By default numpy will complain about dividing with zero values. 
    # We need to change that behaviour because we have a lot of 0 values in our data.
    np.seterr(divide='ignore', invalid='ignore')
    # NDVI formula
    ndvi = (nir - red) / (nir + red)
    return ndvi

NDVI = get_ndvi(nir, red)
```


```python
# Plot the NDVI
plt.figure(figsize=(10,10))
plt.imshow(NDVI, cmap='RdYlGn')

# Add colorbar to show the index
plt.colorbar(fraction=0.03, pad=0.04)
plt.title('NDVI')
# plt.savefig('NDVI.png', dpi = 150)
```




    Text(0.5, 1.0, 'NDVI')




```python
# Data dir
data_dir = "/Users/mac/Desktop/013787851010_01_P001_PSH"

# Output raster
out_tif = os.path.join(data_dir, "NDVI.tif")

# Copy the metadata
out_meta = raster.meta.copy()
out_meta

# Update the metadata
out_meta.update({'driver': 'GTiff',
                 'dtype': 'float32',
                 'nodata': None,
                 'width': raster.shape[1],
                 'height': raster.shape[0],
                 'crs': raster.crs,
                 'count':1,
                 'transform': raster.transform
                })
```


```python
with rasterio.open(out_tif, "w", **out_meta) as dest:
    dest.write(NDVI.astype(np.float32), indexes = 1)
```

## Extracting vegetation area


```python
import copy
vegt_area = copy.copy(NDVI)

# Set Threshold value (it's dependent on area. The value must be manually checked against NRG image in QGIS.)
vegt_area[NDVI<0.25] = np.nan
```


```python
# Let's see the image after extracting
plt.figure(figsize=(10,10))
plt.imshow(vegt_area, cmap='RdYlGn')
plt.colorbar(fraction=0.03, pad=0.04)
plt.clim(vmin=-1, vmax=1)
```



**Export vegetation area into GeoTiff**


```python
# Data dir
data_dir = "/Users/mac/Desktop/013787851010_01_P001_PSH"

# Output raster
out_tif = os.path.join(data_dir, "植生域20OCT13031506.tif")

# Copy the metadata
out_meta = raster.meta.copy()
out_meta

# Update the metadata
out_meta.update({'driver': 'GTiff',
                 'dtype': 'float32',
                 'nodata': None,
                 'width': raster.shape[1],
                 'height': raster.shape[0],
                 'crs': raster.crs,
                 'count':1,
                 'transform': raster.transform
                })
```


```python
with rasterio.open(out_tif, "w", **out_meta) as dest:
    dest.write(vegt_area.astype(np.float32), indexes = 1)
```

# 2. Calculate NDWI and Water Extraction

## NDWI Calculation


```python
# Convert to floats
green = green.astype('f4')
nir = nir.astype('f4')

def get_ndwi(green, nir):
    # By default numpy will complain about dividing with zero values. 
    # We need to change that behaviour because we have a lot of 0 values in our data.
    np.seterr(divide='ignore', invalid='ignore')
    # NDWI formula
    ndwi = (green - nir) / (green + nir)
    return ndwi

NDWI = get_ndwi(green, nir)
```


```python
# Plot the NDWI
plt.figure(figsize=(10,10))
plt.imshow(NDWI, cmap='Blues')

# Add colorbar to show the index
plt.colorbar(fraction=0.03, pad=0.04)
plt.title('NDWI')
# plt.savefig('NDWI.png', dpi = 150)
```




    Text(0.5, 1.0, 'NDWI')





```python
# Data dir
data_dir = "/Users/mac/Desktop/013787851010_01_P001_PSH"

# Output raster
out_tif = os.path.join(data_dir, "NDWI.tif")

# Copy the metadata
out_meta = raster.meta.copy()
out_meta

# Update the metadata
out_meta.update({'driver': 'GTiff',
                 'dtype': 'float32',
                 'nodata': None,
                 'width': raster.shape[1],
                 'height': raster.shape[0],
                 'crs': raster.crs,
                 'count':1,
                 'transform': raster.transform
                })
```


```python
with rasterio.open(out_tif, "w", **out_meta) as dest:
    dest.write(NDWI.astype(np.float32), indexes = 1)
```

## Extracting water area


```python
import copy
wat_area = copy.copy(NDWI)

#set all pixels with NDWI < 0 to nan, keeping only values > 0
wat_area[NDWI<0.25] = np.nan  
```


```python
plt.figure(figsize=(10,10))
plt.imshow(wat_area, cmap='Blues')
plt.colorbar(fraction=0.03, pad=0.04)
plt.clim(vmin=-1, vmax=1)
```


![png](output_22_0.png)


**Export water area into GeoTiff**


```python
# Data dir
data_dir = "/Users/mac/Desktop/013787851010_01_P001_PSH"

# Output raster
out_tif = os.path.join(data_dir, "水域20OCT13031506.tif")

# Copy the metadata
out_meta = raster.meta.copy()
out_meta

# Update the metadata
out_meta.update({'driver': 'GTiff',
                 'dtype': 'float32',
                 'nodata': None,
                 'width': raster.shape[1],
                 'height': raster.shape[0],
                 'crs': raster.crs,
                 'count':1,
                 'transform': raster.transform
                })
```


```python
with rasterio.open(out_tif, "w", **out_meta) as dest:
    dest.write(wat_area.astype(np.float32), indexes = 1)
```

# 3. Calculate Bare Soil Index and Building Extraction

**Create Red-Green-Red image for better visualization**


```python
# Create NRG False color composite
RGR = np.dstack((redn, greenn, redn))
RGR.shape
```




    (9396, 20337, 3)




```python
# In order to export, write requires an array of shape (band, row, col). so we have to reshape the axis
RGR_reshape = np.moveaxis(RGR, [0, 1, 2], [2, 1, 0])
RGR_reshape = np.moveaxis(RGR_reshape, [0, 1, 2], [0, 2, 1])
RGR_reshape.shape
```




    (3, 9396, 20337)




```python
# Data dir
data_dir = "/Users/mac/Desktop/013787851010_01_P001_PSH"

# Output raster
out_tif = os.path.join(data_dir, "RGR_image.tif")

# Copy the metadata
out_meta = raster.meta.copy()
out_meta

# Update the metadata
out_meta.update({'driver': 'GTiff',
                 'dtype': 'float32',
                 'nodata': None,
                 'width': raster.shape[1],
                 'height': raster.shape[0],
                 'count': 3,
                 'crs': raster.crs,
                 'transform': raster.transform
                })

with rasterio.open(out_tif, "w", **out_meta) as dest:
    dest.write(RGR_reshape.astype(np.float32))
```

### Calculate Bare Soil Index


```python
# Convert to floats
green = green.astype('f4')
nir = nir.astype('f4')
red = red.astype('f4')
blue = blue.astype('f4')


def get_bsi(red, green, blue):
    # By default numpy will complain about dividing with zero values. 
    # We need to change that behaviour because we have a lot of 0 values in our data.
    np.seterr(divide='ignore', invalid='ignore')
    # BSI formula
#     bsi = (green + nir) / (green - nir)
    bsi = ((red + blue) - green)/((red + blue) + green)
    return bsi

BSI = get_bsi(red, green, blue)
```


```python
# Plot the NDWI
plt.figure(figsize=(10,10))
plt.imshow(BSI, cmap='Blues')

# Add colorbar to show the index
plt.colorbar(fraction=0.03, pad=0.04)
plt.title('BSI')
# plt.savefig('NDWI.png', dpi = 150)
```




    Text(0.5, 1.0, 'BSI')




![png](output_33_1.png)



```python
# Data dir
data_dir = "/Users/mac/Desktop/013787851010_01_P001_PSH"

# Output raster
out_tif = os.path.join(data_dir, "BSI.tif")

# Copy the metadata
out_meta = raster.meta.copy()
out_meta

# Update the metadata
out_meta.update({'driver': 'GTiff',
                 'dtype': 'float32',
                 'nodata': None,
                 'width': raster.shape[1],
                 'height': raster.shape[0],
                 'crs': raster.crs,
                 'count':1,
                 'transform': raster.transform
                })
```


```python
with rasterio.open(out_tif, "w", **out_meta) as dest:
    dest.write(BSI.astype(np.float32), indexes = 1)
```

## Extracting building


```python
import copy
building = copy.copy(BSI)

# Set Threshold value (it's dependent on area. The value must be manually checked against BSI image and RGR image in QGIS.)
building[BSI<0.14] = np.nan
```

**Export building into GeoTiff**


```python
# Data dir
data_dir = "/Users/mac/Desktop/013787851010_01_P001_PSH"

# Output raster
out_tif = os.path.join(data_dir, "都市20OCT13031506.tif")

# Copy the metadata
out_meta = raster.meta.copy()
out_meta

# Update the metadata
out_meta.update({'driver': 'GTiff',
                 'dtype': 'float32',
                 'nodata': None,
                 'width': raster.shape[1],
                 'height': raster.shape[0],
                 'crs': raster.crs,
                 'count':1,
                 'transform': raster.transform
                })
```


```python
with rasterio.open(out_tif, "w", **out_meta) as dest:
    dest.write(building.astype(np.float32), indexes = 1)
```

**Remove non-building-area**


```python
import fiona
# Read Shape file
with fiona.open("/Users/mac/Desktop/013787851010_01_P001_PSH/non-building-area.shp", "r") as shapefile:
    shapes = [feature["geometry"] for feature in shapefile]

```


```python
import rasterio.mask
# read imagery file
with rasterio.open("/Users/mac/Desktop/013787851010_01_P001_PSH/都市20OCT13031506.tif") as src:
    non_bldg_area, out_transform = rasterio.mask.mask(src, shapes, crop=False)
```


```python
# Mask non-building area from building area image
building_1 = np.where(non_bldg_area > 0, np.nan, building)
building_1
```




    array([[[nan, nan, nan, ..., nan, nan, nan],
            [nan, nan, nan, ..., nan, nan, nan],
            [nan, nan, nan, ..., nan, nan, nan],
            ...,
            [nan, nan, nan, ..., nan, nan, nan],
            [nan, nan, nan, ..., nan, nan, nan],
            [nan, nan, nan, ..., nan, nan, nan]]], dtype=float32)




```python
# Data dir
data_dir = "/Users/mac/Desktop/013787851010_01_P001_PSH"

# Output raster
out_tif = os.path.join(data_dir, "都市20OCT13031506.tif")

# Copy the metadata
out_meta = raster.meta.copy()
out_meta

# Update the metadata
out_meta.update({'driver': 'GTiff',
                 'dtype': 'float32',
                 'nodata': None,
                 'width': raster.shape[1],
                 'height': raster.shape[0],
                 'crs': raster.crs,
                 'count':1,
                 'transform': raster.transform
                })
```


```python
with rasterio.open(out_tif, "w", **out_meta) as dest:
    dest.write(building_1.astype(np.float32))
```


```python

```

