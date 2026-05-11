# Cross-Regional Transfer Learning for Landslide Susceptibility Modelling

![Project overview image](../assets/images/project1-cover.png)

## Overview

This project applies cross-regional transfer learning (TL) to predict landslide susceptibility in data-scarce regions of Kenya, using a Support Vector Machine (SVM) model trained on West Pokot County (data-rich source) and transferred to Elgeyo Marakwet County (data-scarce target). By leveraging nine time-independent landslide conditioning factors derived from remote sensing and GIS data, the study demonstrates that transfer learning can deliver reliable hazard maps without the need for extensive local landslide inventories — directly supporting disaster preparedness and land-use planning in vulnerable communities.

**Study Area:** West Pokot County (source) & Elgeyo Marakwet County (target), Kenya  
**Duration:** January 2025 – May 2025  
**Role:** Solo project  
**Status:** Completed

---

## Methods & Tools

**Data Sources**

- SRTM Digital Elevation Model (USGS, 30m) — elevation, slope, aspect, curvature, TWI
- Landsat 8 OLI (USGS, 30m) — NDVI (vegetation cover)
- Landslide Inventory Data (Global Precipitation Measurement Mission)
- Lithology Data (Water Resource Authority, 30m)
- Roads, Rivers & Streams shapefiles (DIVA-GIS / OpenStreetMap, 30m)

**Processing Steps**

1. Prepared landslide (positive) and non-landslide (negative) point datasets using random sampling with spatial buffers; applied a 70:30 train-test split
2. Derived nine time-independent landslide conditioning factors (slope, aspect, curvature, elevation, NDVI, TWI, lithology, distance to roads, distance to rivers) for both regions
3. Assessed multicollinearity using Variance Inflation Factor (VIF) and Tolerance to confirm all predictors were independent enough for modelling
4. Trained an SVM model with RBF kernel on West Pokot data; optimised hyperparameters (C and gamma) via grid search with cross-validation
5. Transferred the trained model directly to Elgeyo Marakwet without retraining, generating landslide susceptibility maps for both counties
6. Evaluated model performance using precision, recall, F1-score, accuracy, Cohen's kappa, RMSE, and MAE

**Tools Used**

| Tool | Purpose |
|------|---------|
| R | Multicollinearity analysis, SVM model training & evaluation |
| QGIS | Preparation of landslide conditioning factor layers & cartography |
| ArcMap | Visualisation and finalisation of susceptibility maps |
| Google Earth Engine (GEE) | NDVI derivation from Landsat 8 imagery |
| Python | Supporting data preprocessing and automation |

---

## Key Findings

- The SVM model achieved **91.53% accuracy and an F1-score of 91.06%** in West Pokot (source region), confirming strong baseline performance
- After transfer to Elgeyo Marakwet, the model maintained **83.33% accuracy and an F1-score of 80.0%** — without any retraining on local data
- **Elevation and Distance to Roads** were the dominant landslide predictors in West Pokot, reflecting the influence of rugged topography and road-induced slope disturbance
- **Distance to Rivers** was the most critical factor in Elgeyo Marakwet (~60% relative importance), driven by the escarpment terrain and fluvial erosion along the Kerio River system
- All VIF values remained below 10 in both counties, confirming no severe multicollinearity among the nine conditioning factors
- High-susceptibility zones in Elgeyo Marakwet were concentrated in the central and northern wards (Embobut, Arror, Kaben, Chesoi), aligning with historically reported landslide-affected areas
- The study validates transfer learning as a **cost-effective alternative to field-intensive inventory collection** for landslide hazard mapping in data-scarce sub-Saharan African regions

---
