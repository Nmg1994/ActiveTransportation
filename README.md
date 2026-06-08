# Transportation and Urban Health Simulation Model

This repository presents an agent-based transportation simulation framework developed for urban mobility and public health analysis in the Montreal metropolitan area. The model integrates a multimodal transportation network (road, bicycle, transit), demographic data, and spatial infrastructure to simulate individual travel behavior and mode choice decisions.

---

## Project Overview

The model simulates daily mobility decisions of synthetic agents (residents) based on:

- Home–work/school accessibility
- Transportation network structure
- Availability of BIXI bike stations and STM transit stations
- Individual socio-demographic attributes (age, income, location)
- Travel time and distance constraints

Agents choose between four transportation modes:
- Car
- Public Transit
- Bicycle
- Walking

---

## Study Area

The model is built for the Montreal region using:

- Dissemination Areas (DA) from Statistics Canada
- Road network extracted from clipped shapefiles
- Public transit (STM) stations
- Bicycle-sharing (BIXI) stations
- Residential, workplace, and school datasets

To ensure spatial continuity, the road network is processed using a dissolved study-area boundary.

---

## Methodology

### 1. Network Construction

A directed multimodal transportation network is built using `NetworkX`:

- Nodes represent intersections
- Edges represent road segments
- Edge attributes include:
  - Length (km)
  - Speed (km/h)
  - Travel time (min)
  - Mode restrictions (car, bike, pedestrian access)

A `MultiDiGraph` structure is used to support multiple directed edges between nodes.

---

### 2. Spatial Processing

All spatial data is processed using `GeoPandas`:

- Clipping to study area
- Dissolving administrative boundaries using PRUID
- Spatial assignment of infrastructure to nearest network nodes

---

### 3. Agent-Based Model

Each agent represents a synthetic individual with:

- Age group (child or adult)
- Income level
- Residential location (node in network)
- Assigned workplace or school

Agents make travel decisions based on:

- Generalized travel cost
- Accessibility to infrastructure
- Distance to transit and bike-sharing stations
- Socio-demographic factors

---

### 4. Destination Choice

- Adults: workplace selection based on network accessibility
- Children: school selection within increasing radius search
- Infrastructure proximity is evaluated using shortest path distances

---

### 5. Mode Choice Model

A discrete choice model is implemented using utility functions:

- Auto
- Transit
- Bicycle
- Walking

Utilities depend on:

- Travel time
- Income
- Age
- Bike lane availability
- BIXI and STM accessibility

Probabilities are computed using a logit model.

---

## Key Features

- Multi-modal transportation network modeling
- Integration of GIS and agent-based simulation
- Realistic accessibility-based destination choice
- Infrastructure sensitivity (BIXI, STM, bike lanes)
- Scalable agent generation from census data

---

## Data Inputs

The model uses the following datasets:

- Montreal Dissemination Areas (DA)
- Road network (nodes and edges shapefiles)
- Residential land use polygons
- Workplace locations
- School locations
- BIXI station locations
- STM transit station locations

---
