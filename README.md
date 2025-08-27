# Bangweulu Insurance Zone Mapping

**Author:** Elkana Kipruto  
**Date:** 10th May 2025  
**Notebook:** `bangweulu_assessment.ipynb`

---

## Project Overview

This project demonstrates how satellite Earth Observation (EO) data and geospatial analysis can be used to delineate **insurance zones** for agricultural resilience.  
The study area is **Bangweulu, Zambia**, and the analysis explores two approaches:

1. **NDVI-only Zones:** Using vegetation greenness (Normalized Difference Vegetation Index) as the sole metric.
2. **Multi-Criteria Decision Analysis (MCDA):** Combining NDVI with other environmental factors such as precipitation, soil moisture, elevation, and ESA WorldCover land use.

The goal is to identify **homogeneous zones** for crop insurance schemes by understanding vegetation health and its relationship to environmental variables.

---

## Key Objectives

- Assess vegetation health before and after certain periods using **Sentinel-2 NDVI**.
- Generate **UAI (Unit Area of Insurance) zones** based on NDVI thresholds.
- Enhance UAI zones using **MCDA**, integrating multiple environmental datasets.
- Create **time-series NDVI trends (2020–2024)** for each zone.
- Export results as GeoTIFFs for further visualization and decision-making.

---

## Methodology

### 1. **Environment Setup**
- Google Earth Engine Python API
- Google Colab for interactive development
- Libraries: `pandas`, `geopandas`, `geemap`, `matplotlib`, `seaborn`, `numpy`

### 2. **Data Sources**
- **Sentinel-2 SR** (Surface Reflectance): NDVI & cloud-masked composites
- **ESA WorldCover 2020**: Land cover for vegetation masking
- **CHIRPS**: Precipitation dataset
- **MODIS MCD15A3H**: Leaf Area Index (LAI)
- **NASA SMAP**: Soil moisture data

### 3. **Processing Steps**
- **Cloud masking:** Using Sentinel-2 cloud probability (<40%)
- **NDVI computation:** `(NIR - RED) / (NIR + RED)`
- **Vegetation mask:** ESA WorldCover to isolate vegetation classes
- **NDVI classification:** Wetlands, shrubland, cropland, evergreen using thresholds
- **UAI zoning:** Segmentation into 0.2 NDVI intervals
- **MCDA zoning:** Weighted sum of normalized NDVI (0.5), LAI (0.2), precipitation (0.2), soil moisture (0.1)
- **Time-series analysis:** Monthly NDVI (2020–2024) per zone
- **Visualization:** Line plots & interactive maps

### 4. **Outputs**
- Static PNG plots: NDVI-only and MCDA NDVI time series
- Interactive layers in GEE Map
- Exported GeoTIFFs:
  - Vegetation mask
  - Classified vegetation (wetlands/shrub/crop/evergreen)
  - UAI NDVI zones
  - UAI MCDA zones
  - Mean NDVI and masked NDVI

---

## Results & Insights

- **NDVI-based zones** provide a simple segmentation based on vegetation greenness.
- **MCDA-based zones** offer a more nuanced classification incorporating climate and soil factors.
- NDVI time series show how vegetation health varies seasonally and across zones.
- Exported layers can support **insurance scheme design** and **agricultural risk assessment**.

---

## Repository Contents

- `bangweulu_assessment.ipynb`: Main analysis notebook
- Project Outputs: `https://bangweulu-assessment.vercel.app/`,
