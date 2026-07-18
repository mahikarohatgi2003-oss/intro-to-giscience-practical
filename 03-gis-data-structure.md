# Chapter 3 — GIS Data Structure

## 3.1 GIS Data: Introduction

Data is the most important component of a GIS. Geographic data and related tabular data can be collected in-house or bought from a commercial provider. Most GIS use a DBMS to create and maintain a database that organizes and manages this data — anything bearing a definable relationship to space, including data about things and events occurring in nature.

Historically this consisted of hard-copy data: cartographic maps, surveyor's logs, demographic statistics, geographic reports, and field descriptions. Advances in spatial data collection, classification, and accuracy have made standard digital base-maps available at many scales.

## 3.2 GIS Data: Types

### Vector Data
Represents geographic features as points, lines, polygons, or combinations of these.

| Type | Definition | Examples |
|---|---|---|
| **Point** | One pair of coordinates (x, y); dimensionless | Cities, wells, villages |
| **Line** | At least two coordinate pairs, connecting a minimum of two points | Roads, railway tracks, streams |
| **Polygon** | A closed line with area; minimum of three coordinate pairs | City extents, forests, land use zones |

### Raster Data
Made up of pixels — an array of grid cells organized in columns and rows. Every geographic feature is represented only through pixels; there is no point/line/polygon distinction. Each pixel holds a single value (unlike vector features, which may carry multiple attributes), so representing multiple features (land use, soil type, forest density, topography, etc.) requires multiple raster layers.

## 3.3 Spatial and Non-Spatial Data

- **Spatial data** is the geographic representation of features — what's rendered as maps of real-world features on screen. It divides into vector and raster data.
- **Non-spatial (attribute) data** describes the characteristics of spatial features — often called tabular data (e.g. names of roads, places, schools).

## 3.4 Raster and Vector Data Structures

### Raster Data Structure
The simplest raster structures consist of an array of grids. Each cell, referenced by row and column number, contains a value representing the mapped attribute. A point is a single grid cell; a line is a set of neighbouring cells. Common storage methods include chain code, run-length code, and quadtrees.

### Vector Data Structure
Vector representation attempts to represent an object as exactly as possible. The coordinate space is continuous (not quantized, as in raster), so positions, lengths, and dimensions can be defined precisely.
- **Point entities** embrace all geographic/graphical entities positioned by a single coordinate signal.
- **Polygon data structure** aims to describe the topological properties of areas so that associated properties can be displayed and manipulated as thematic map data.
