# Chapter 2 — Global Positioning System (GPS)

## 2.1 GPS: Introduction

Geoprocessing is a framework and set of tools for processing geographic and related data. The comprehensive suite of geoprocessing tools can be used to perform spatial analysis or manage GIS data in an automated way, and is a core part of day-to-day work in platforms such as ArcGIS Pro.

A typical geoprocessing tool operates on a dataset — a feature class, raster, or table — and produces an output dataset. For example, the **Buffer** tool takes features as input, creates buffer areas around them to a specified distance, and writes the buffers to a new output dataset.

Beyond the built-in tool suite, geoprocessing is also a framework that supports control of the processing environment and lets users build custom tools to further automate and scale their workflows.

## 2.2 Components of GPS

A GPS system consists of three components working together as a single unit:

| Component | Segment | Role |
|---|---|---|
| **Satellites** | Space Component | Orbit the earth |
| **Ground Stations** | Control Component | Monitor and manage satellites |
| **Receivers** | User Component | Determine user location |

![GPS segments diagram](../assets/diagrams/gps-segments-diagram.png)

### Satellites (Space Component)
Orbit the earth at an altitude of ~20,000 km, completing an orbit roughly every 12 hours.
- Orbits are designed so 6 satellites are always within line of sight from any location on earth.
- At least 4 satellites are available for observation at any time, anywhere in the world, year-round.
- Satellites act like stars in a constellation — their locations are known because they continuously send out signals.

### Ground Stations (Control Component)
Comprise three sub-components:
- Master Control System
- Monitor Station
- Ground Antenna

Key functions:
- Checking the movement and proper functioning of satellites.
- Using radar to confirm satellite position.

### Receivers (User Component)
GPS receivers are present in smartphones, tablets, PCs, etc. They:
- Estimate distance to visible satellites.
- Once distance from 4+ satellites is calculated, determine the receiver's exact location.

## 2.3 Principles and Uses of GPS

- **Emergency Response** — First responders use GPS for mapping, weather tracking/prediction, and tracking emergency personnel. In the EU and Russia, the eCall regulation relies on GLONASS (a GPS alternative) and telematics to notify emergency services after a vehicle crash, cutting response time.
- **Entertainment** — GPS powers location-based games and activities like Pokémon Go and Geocaching.
- **Health and Fitness** — Smartwatches and wearables track activity (e.g. running distance) and benchmark it against similar demographics.
- **Construction, Mining, and Off-Road Trucking** — From locating equipment to improving asset allocation, GPS boosts return on assets.
- **Transportation** — Logistics companies use telematics for route optimization, fuel efficiency, driver safety, and compliance.
- **Location** — Finding the exact position of any object.
- **Navigation** — Assisting movement from one place to another.
- **Tracking** — Monitoring the movement of an object.
- **Mapping** — Creating maps of a place or the whole world.
- **Timing** — Taking precise time measurements.
- **Defence** — Used for accurate targeting and attack operations.
