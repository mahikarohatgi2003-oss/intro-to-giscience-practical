# Chapter 4 — GIS Data Analysis

One of the most important characteristics of GIS is its capability for data analysis and spatial modeling. Conventional GIS analysis and manipulation capabilities include map overlaying, reclassification, proximity analysis, buffering, and other cartographic tools computed as a function of independent values associated with locations across two or more existing maps.

All exercises in this chapter use **West Bengal, India** as the study area, with administrative data sourced from the **Census of India, 2011**.

---

## 4.1 Data Analysis: Georeferencing

Georeferencing relates the internal coordinate system of a map or aerial photo image to a geographical coordinate system. The most visible effect is that display software can then show ground coordinates and measure ground distances/areas. In other words, georeferencing associates a digital image file with locations in physical space. A "geographical object" broadly refers to anything that can reasonably be related to a location — points of interest, roads, places, bridges, buildings, or agricultural areas (Hackeloeer, 2014).

### Importance of Georeferencing
- Makes aerial/satellite raster imagery usable for mapping by relating it to other data (e.g. GPS points).
- Different maps use different projection systems; georeferencing tools combine and overlay them with minimum distortion.
- Helps "flatten" curved regions into a flat surface for referencing.
- Ties surveyed reference points back to topographic maps.
- Establishes relationships between social survey results and geography.

### Steps: Georeferencing in QGIS
1. Open QGIS → **New Empty Project**.
2. Open the map from the Browser panel → **Raster** menu → **Georeferencer**.
3. In the dialog box, click **Open Raster**.
4. Browse to and select the image to be georeferenced.
5. In the Georeferencer window (raster display on top, GCP table below), set the raster's Coordinate Reference System (CRS):
   - Go to **Transformation Settings** → **Target SRS**.
   - For GPS coordinates in WGS84, choose **EPSG:4326**.
6. Assign coordinates to at least 4 points using the coordinate grid markings:
   - Click **Add Point** in the toolbar.
   - Enter X (longitude) and Y (latitude) in the popup → **OK**. The GCP table updates with each point.
   - Add 4–5+ GCPs spread across the whole image — more points improve registration accuracy.
7. Under **Settings → Transformation Settings**, set **Target SRS** to Project CRS (EPSG:4326 – WGS 84) and check **Save GCP points** → **OK**.
8. In the Georeferencer window: **File → Start Georeferencing** — this warps the image using the GCPs and creates the target raster.
9. The georeferenced image loads automatically into QGIS.

![Figure 1 — Georeferenced Map of West Bengal](../assets/figures/figure-01-georeferenced-map.jpg)

---

## 4.2 Digitisation and Editing

Vector data uses points and x, y coordinates to construct spatial features:
- **Point entities** — discrete locations too small to depict as lines/areas (e.g. well location, telephone pole).
- **Line entities** — features built from straight-line segments of two or more coordinates.
- **Area entities** — polygons; the simplest representation extends the simple chain concept, listing each polygon as a set of XY boundary coordinates.

### Steps: Map-Making / Digitisation in QGIS
1. Open QGIS.
2. Georeference the base map first (see §4.1).
3. Drag the georeferenced map into the Layers panel.
4. Create a shapefile for the map, selecting the **Polygon** feature type, and save it to a folder.
5. Enable **Toggle Editing** and draw polygons on the georeferenced map. Use the **Split Feature** tool where district boundaries divide.
6. Open the shapefile's **Attribute Table**, enable editing, and add a field named `Districts`. Select each polygon (via **Select Features**) and enter its district name. Save edits.
7. Open **Properties → Symbology → Categorized**, and classify the map — this applies distinct colors per category.
8. Go to **New Print Layout** to export the map.
9. In the layout view, add a title, grid, frame, legend, scale bar, and north arrow.
10. Export the finished layout as an image to the desired location.

![Figure 2 — Administrative Map of West Bengal](../assets/figures/figure-02-administrative-map.png)

---

## 4.3 Data Analysis: Query (SQL)

A spatial query is a special database operation (via geodatabases/spatial databases) that differs from non-spatial queries in that it supports geometry data types — points, lines, and other shapes. Queries let users extract desired, selected features.

Query/SQL (Standard Query Language) selection can be performed in four ways:
1. Select a Feature by Polygon
2. Select a Feature by Freehand
3. Select a Feature by Radius
4. Select a Feature using an Expression

### 1. Select a Feature by Polygon
1. Add the digitized "Map of WEST BENGAL" shapefile to the map view.
2. Choose the **Select Features by Polygon** tool.
3. Click on the map and draw a polygon around the regions to select.
4. Selected features highlight yellow and appear selected in the attribute table.

![Select by polygon](../assets/screenshots/select-by-polygon.png)

### 2. Select a Feature by Freehand
1. In the **Select Features** dropdown, choose **Select Features by Freehand**.
2. Click and drag to draw a freehand shape over the features to select.

![Select by freehand](../assets/screenshots/select-by-freehand.png)

### 3. Select a Feature by Radius
1. Choose **Select Feature by Radius** from the Select Features dropdown.
2. Click and set the desired radius to form a circle around the districts to be selected.

![Select by radius — step 1](../assets/screenshots/select-by-radius-01.png)
![Select by radius — step 2](../assets/screenshots/select-by-radius-02.png)

### 4. Select Features Using an Expression

**a) Select feature by Value**
1. Choose **Select feature by Value** from the Select Features dropdown.
2. In the dialog, enter the feature detail to extract (e.g. district names starting with "D") and click **Select Features**.

![Select by value](../assets/screenshots/select-by-value.png)

**b) Select a Feature by Expression**

This mode offers multiple operators for flexible querying:
1. Click **Select features by expression**.
2. In the **Field and Values** panel, choose the attribute variable to query.
3. Click the operators expression list to see available operators.

![Select by expression](../assets/screenshots/select-by-expression.png)

**Expression operator examples used in this exercise:**

| Operator | Syntax example | Notes |
|---|---|---|
| `LIKE` | `"Dist." LIKE 'S%'` | Case-sensitive pattern match |
| `ILIKE` | `"Dist." ILIKE 'e%'` | Case-*insensitive* version of LIKE |
| `AND` | `"TOT_M" > '1000000' AND "TOT_F" > '200000'` | Combines two conditions |
| `IN` | `'Hugli' IN (District)` | Membership test |
| `OR` | `"P_LIT" < '4' OR "P_ILL" < '2000000'` | Either condition true |

![LIKE operator](../assets/screenshots/expression-like-operator.jpg)
![ILIKE operator](../assets/screenshots/expression-ilike-operator.jpg)
![AND operator](../assets/screenshots/expression-and-operator.png)
![IN operator](../assets/screenshots/expression-in-operator.jpg)
![OR operator](../assets/screenshots/expression-or-operator.jpg)

---

## 4.4 Data Analysis: Geoprocessing

Geoprocessing is a framework and set of tools for processing geographic and related data — used to perform spatial analysis or manage GIS data in an automated way, and central to day-to-day GIS work.

A typical geoprocessing tool operates on a dataset (feature class, raster, or table) and produces a resulting output dataset. Beyond individual tools, geoprocessing is also a framework supporting custom, chained automation of repetitive or complex tasks.

QGIS offers several core geoprocessing tools, demonstrated below on West Bengal's districts:

### 1. Buffer
A buffer is a zone around a map feature measured in units of distance or time — useful for proximity analysis. It's the bounding region defined by points at a specified maximum distance from all nodes along an object's segments. The **segments** parameter controls how many line segments approximate a quarter-circle when creating round offsets; the **end cap style** parameter controls how line endings are handled.

**Path:** Vector (top ribbon) → Geoprocessing Tools → Buffer

![Figure 3 — Buffer Map of West Bengal](../assets/figures/figure-03-buffer-map.png)

*Here, the Bardhaman district is buffered.*

### 2. Clip
Clip is an overlay function that cuts an input layer down to the extent of a defined feature boundary — like using a cookie cutter. To clip, you need points/lines/polygons as input and a polygon as the clipping extent; the preserved data is the clip result.

**Path:** Vector → Geoprocessing Tools → Clip

Select the West Bengal vector layer and check "Selected features only" to clip just a particular portion.

![Figure 4 — Clip Map in West Bengal](../assets/figures/figure-04-clip-map.png)

*Here, clipping is performed on the Bardhaman district.*

### 3. Convex Hull
The convex hull is the polygon with the shortest perimeter enclosing a set of points — like a rubber band stretched around a set of nails on a board.

**Path:** Vector → Geoprocessing Tools → Convex Hull. Fill required details, run on selected features to see the reshaped output.

![Figure 5 — Convex Hull Map of West Bengal](../assets/figures/figure-05-convex-hull-map.png)

*Here, the Bardhaman district is convex-hulled.*

### 4. Dissolve
Dissolve erases internal borders and unifies features into one — e.g. dissolving country boundaries sharing a continent attribute into a single continent shape.

Analogy: the Berlin Wall dissolving East and West into a single country; or North India + South India = India.

![Figure 6 — Dissolve Map of West Bengal](../assets/figures/figure-06-dissolve-map.png)

### 5. Union
The union tool spatially combines two data layers, preserving features from both layers to their full extent — it maintains all input feature boundaries and attributes in the output, which can get visually "messy" with more overlaps.

![Figure 7 — Union Map of West Bengal](../assets/figures/figure-07-union-map.png)

---

## 4.5 Data Analysis: Thematic Map

A thematic map (also called a special-purpose, single-topic, or statistical map) shows the spatial distribution of one specific data theme for selected geographic areas — e.g. population density or income — as opposed to a reference map, which focuses on the location/name of features. Thematic maps still typically include some locational context to help orient readers.

### Choropleth Map
Choropleth maps represent statistical data via shading patterns, symbols, or predetermined geographic areas (e.g. countries/districts), making spatial variability of a measurement easy to read.

**Steps:**
1. Open QGIS and add the vector layer (here, West Bengal).
2. Go to **Properties → Symbology → Graduated**, and select the desired value (here, Density of Population).

![Figure 8 — Density of West Bengal](../assets/figures/figure-08-density-map.png)

### Pie Diagram
A pie chart divides a circle into slices to illustrate numerical proportion — arc length (and therefore central angle/area) is proportional to the represented quantity. Pie charts give a quick read on proportional distribution across categories, summing to 100%.

**Proportionate circles** show a divisible quantity (e.g. population) split into component parts (e.g. ethnic groups); circle size can itself also represent magnitude of data.

![Figure 9 — Literacy Rate of West Bengal](../assets/figures/figure-09-literacy-map.png)

### Histogram
A histogram summarizes discrete or continuous data, visually showing how many data points fall within specified "bins." Unlike a vertical bar graph, histogram bars have no gaps between them. Histograms reveal data distribution, frequency, median, and any outliers or gaps.

**Steps:**
1. Open QGIS and load the relevant vector layer/map.
2. Go to layer **Properties → Diagrams → Histogram**.
3. Choose the attribute(s) to display (here, population data).
4. Specify bar size/placement → **Apply** → **OK**.
5. Add labels to the shapefile to complete the one-dimensional representation.

![Figure 10 — Population Composition of West Bengal](../assets/figures/figure-10-population-composition-map.png)
