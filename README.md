# Dataset and Code Repository for: Inferring Multi-Scale Bedforms from Water Surface Patterns in a Sediment-Rich River Reach via UAV Orthoimagery

## Paper Information

**Title**: Inferring Multi-Scale Bedforms from Water Surface Patterns in a Sediment-Rich River Reach via UAV Orthoimagery

**Authors**: Tao Wang¹, Jianing Liu¹, Yucheng Liu¹, Xingyu Chen¹, Jing Yuan¹, Xudong Fu¹

**Affiliation**: ¹Department of Hydraulic Engineering, Tsinghua University, Beijing, China

**Corresponding Authors**: Xudong Fu (xdfu@tsinghua.edu.cn), Jing Yuan (yuanj2021@gmail.com)

**Manuscript Submitted to**: JGR: Earth Surface

---

## Repository Overview

This repository contains all the code, raw/processed data, and auxiliary materials required to reproduce the results presented in the above manuscript. The materials are closely aligned with the study’s core methods (variance analysis for large-scale primary dunes, Fourier analysis for small-scale secondary dunes) and validation processes (against MBES bathymetry), covering the Tongguan reach of the Yellow River study area.

All materials are provided to ensure the reproducibility of the study’s findings, including dune geometry extraction, water surface wave analysis, and hydraulic impact assessment.

---

## Directory Structure and Detailed Content Description

### 1. Code Folder (Core Algorithm Implementation)

This folder contains the core algorithm code corresponding to the methods proposed in the manuscript, with each file strictly matching the analytical procedures described in Sections 3 and 4 of the paper. Detailed descriptions are as follows:

- **LargeDune_Variance.ipynb**: Implements the sliding-window variance analysis method (Section 3.2) for detecting the lee sides of large-scale primary dunes (λ > 10 m). The code processes grayscale UAV orthoimagery to compute local pixel-intensity variance, perform adaptive thresholding, and extract wave-cluster zones (proxy for dune lee sides). A set of sample UAV orthoimagery data is stored in the `UAV bedform` subfolder, consistent with the pre-flood survey data (July 26, 2025) used for validation in Section 3.3.

- **SmallDune_Fourier.ipynb**: Implements the two-dimensional Fourier spectral analysis method (Section 4.2) for extracting the dominant wavelength and orientation of small-scale secondary dunes (λ < 10 m). The code performs detrending, 2D FFT, spectral filtering, and dominant signal extraction, matching the validation process against MBES bathymetry described in Section 4.3. Two sets of sample data (UAV orthoimagery and corresponding MBES DEM) are stored in the `MBS_data` subfolder.

- **MBS_swath_centerline.ipynb**: Combines sliding window and Fourier analysis to calculate and compare the dominant orientations of water surface waves (from UAV orthoimagery) and riverbed bedforms (from MBES DEM). This code supports the validation of bedform-induced surface wave orientation (Section 4.3, Fig. 10), where surface wave orientation is shown to be consistent with bedform orientation (RMSE = 10.49°). The data used in this code is also stored in the `MBS_data` subfolder.

### 2. Media Folder

This folder stores UAV-acquired videos and photographs of the Tongguan reach, providing additional visual examples of water surface patterns observed in the study. These include: (1) stationary gravity waves (signature of secondary dunes), (2) wave clustering/rarefaction and surface boils (signature of primary dunes), and (3) wind-generated waves (used for background noise exclusion, Section 2.4). The materials supplement the figures in the manuscript (e.g., Figs. 6, 7, 12) and help illustrate the surface signatures of different-scale bedforms.

### 3. tif data Folder

This folder contains georeferenced geotif data, including: (1) UAV orthoimagery and (2) MBES bathymetric topography, consistent with the data described in Sections 2.2 and 2.3 of the manuscript.

- **UAV Orthoimagery**: Combined geotif data of UAV orthomosaics collected from July 26 to August 2, 2025 (covering pre-flood, sediment peak, and post-flood periods of the 2025 field campaign). Imagery was acquired 1–2 times per day (morning and evening) using a DJI Mavic 3E UAV with RTK module, at altitudes of 300–500 m (GSD: 0.12–0.15 m) and >90% image overlap. Examples with poor lighting conditions (e.g., broken cloud cover, low sun angles) are also preserved. Due to temporary equipment failure, no imagery was collected on the afternoon of July 26 (July26pm) and the afternoon of August 2 (August2pm).

- **MBES Bathymetry**: High-resolution bathymetric DEM data acquired on July 26, 2025 (Q = 572 m³/s, Cv = 5.1 kg/m³) using a ship-borne R2Sonic 2024 multi-beam echosounder (MBES). The data was post-processed in CARIS software with RTK positioning and motion correction, serving as the ground-truth benchmark for validating the UAV-based dune extraction method (Sections 3.3 and 4.3). Additionally, dune length (λ) and height (A) of several large-scale primary dunes were manually extracted from the MBES DEM to verify the applicability of empirical scaling relations (Section 2.2.2, Fig. 3).

### 4. Full size figure Folder

This folder stores the full-size, high-resolution versions of all figures presented in the main text of the manuscript (e.g., Figs. 1–12). These figures include study area location, hydrograph/sedigraph, bedform profiles, validation results, and bedform distribution maps, facilitating detailed inspection and reuse of the study’s key visualizations.

---

## Notes

1. **Data and Code Consistency**: All code and data in this repository are strictly consistent with the methods, results, and analysis of the corresponding manuscript. For detailed technical details (e.g., parameter settings for variance analysis, FFT filtering thresholds), theoretical basis, and validation metrics, please refer to the main text of the paper.

2. **Data Limitations**: The MBES data stored in this repository was collected under relatively low sediment concentration conditions (Cv = 5.1 kg/m³). As noted in Section 2.2.1, MBES effectiveness is severely compromised under high sediment concentrations (e.g., Cv = 85.4 kg/m³ during the sediment peak), which motivated the development of the UAV-based method.

3. **Usage Guidance**: The code is designed to be run with the provided sample data. For application to other study areas, users should adjust parameters (e.g., sliding window size, thresholding criteria, FFT cutoff wavelength) based on local hydrological and morphological conditions, as described in Sections 3.2 and 4.2 of the manuscript.

4. **Acknowledgments**: This research is funded by China’s MST Key R&D (Grant 2023YFC3206201). We thank the Yellow River Conservancy Commission for providing hydrological data, and Yiheng Ji (Tsinghua University) and Peng Lin (Tianjin University) for assistance with field surveys.
