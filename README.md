# Introduction to GIScience (Practical) — West Bengal

A GIS practical file covering core geospatial concepts and a hands-on QGIS workflow — georeferencing, digitization, spatial querying (SQL expressions), geoprocessing (buffer, clip, convex hull, dissolve, union), and thematic mapping (choropleth, pie diagram, histogram) — applied to the state of **West Bengal, India**, using **Census of India 2011** data.

> Submitted for B.A. (Honours) Geography, Semester IV, Paper: *Introduction to GIScience (Practical)* — Unique Paper Code 12293405, Department of Geography, Kalindi College, University of Delhi (2022–2023).

## Contents

| Chapter | Topic |
|---|---|
| [Chapter 1](docs/01-introduction-to-gis.md) | Introduction to GIS — definitions, evolution, components |
| [Chapter 2](docs/02-global-positioning-system.md) | Global Positioning System (GPS) — components, principles, uses |
| [Chapter 3](docs/03-gis-data-structure.md) | GIS Data Structure — vector vs. raster, spatial vs. non-spatial |
| [Chapter 4](docs/04-gis-data-analysis.md) | GIS Data Analysis — georeferencing, digitization, SQL queries, geoprocessing, thematic maps *(core practical work)* |
| [Chapter 5](docs/05-applications-of-gis.md) | Applications of GIS — land use mapping, urban sprawl, forest monitoring |
| [Chapter 6](docs/06-conclusion.md) | Conclusion |
| [References](docs/references.md) | Cited sources |

## Repository Structure

```
.
├── README.md
├── LICENSE
├── docs/                     # Chapter-by-chapter write-up (Markdown)
│   ├── 01-introduction-to-gis.md
│   ├── 02-global-positioning-system.md
│   ├── 03-gis-data-structure.md
│   ├── 04-gis-data-analysis.md
│   ├── 05-applications-of-gis.md
│   ├── 06-conclusion.md
│   └── references.md
├── data/
│   └── west_bengal_census_2011.csv   # Appendix table, Census of India 2011
└── assets/
    ├── figures/               # The 10 numbered figures from the original file
    ├── screenshots/           # Step-by-step QGIS process screenshots (SQL queries)
    └── diagrams/              # Conceptual diagrams (GIS components, GPS segments)
```

## Figures

| # | Title | File |
|---|---|---|
| 1 | Georeferenced Map of West Bengal | `assets/figures/figure-01-georeferenced-map.jpg` |
| 2 | Administrative Map of West Bengal | `assets/figures/figure-02-administrative-map.png` |
| 3 | Buffer Map of West Bengal | `assets/figures/figure-03-buffer-map.png` |
| 4 | Clip Map in West Bengal | `assets/figures/figure-04-clip-map.png` |
| 5 | Convex Hull Map of West Bengal | `assets/figures/figure-05-convex-hull-map.png` |
| 6 | Dissolve Map of West Bengal | `assets/figures/figure-06-dissolve-map.png` |
| 7 | Union Map of West Bengal | `assets/figures/figure-07-union-map.png` |
| 8 | Density of West Bengal | `assets/figures/figure-08-density-map.png` |
| 9 | Literacy Rate of West Bengal | `assets/figures/figure-09-literacy-map.png` |
| 10 | Population Composition of West Bengal | `assets/figures/figure-10-population-composition-map.png` |

## Data Source

District-level population, sex, and literacy data: **Census of India, 2011** — see [`data/west_bengal_census_2011.csv`](data/west_bengal_census_2011.csv).

## Software Used

- **QGIS** (open-source GIS) — georeferencing, digitization, attribute editing, spatial SQL, geoprocessing, symbology/thematic mapping.

## Author

**Mahika Rohatgi**
B.A. (Hons) Geography, Kalindi College, University of Delhi
[GitHub](https://github.com/mahikarohatgi) · [LinkedIn](https://linkedin.com/in/mahika-rohatgi) · rohatgimahika@gmail.com

## License

Written content and figures are original coursework by the author. See [`LICENSE`](LICENSE) for terms.
