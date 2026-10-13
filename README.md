# Multi-scale UAV Mapping of Plaka Park, Lesvos Petrified Forest Geopark

Multi-scale UAV documentation of the western section of Plaka Park (Lesvos UNESCO Global Geopark) across two spatial resolution tiers: a comprehensive park-scale overview (GSD 3.23 cm/px) and an ultra-detailed single fossil site survey (GSD 0.67 cm/px). The survey integrates drone photogrammetry (DJI Mavic 3 Enterprise RGB) and aerial LiDAR (DJI Matrice with Zenmuse L1) to produce dense point clouds, high-resolution 3D textured meshes, standardized orthophoto map layouts, a bare-earth DEM with 1 m contours, and quantitative cloud-to-cloud (C2C) comparative analyses.

## Key results

| Metric / Parameter | Value |
|---|---|
| Fieldwork date | 26 April 2026 |
| Sensors | DJI Mavic 3 Enterprise (RGB) & DJI Matrice with Zenmuse L1 (LiDAR) |
| Coordinate Reference System | WGS 84 / UTM zone 35N (EPSG:32635) |
| Park-scale point cloud (Mavic 3E) | 35.0 million points, GSD 3.23 cm/px |
| Fossil-site point cloud (Mavic 3E) | 34.4 million points, GSD 0.67 cm/px (18,852 pts/m²) |
| Park vs. Fossil Site (Cloud-to-Cloud) | Mean: 0.054 m, RMS: 0.070 m |
| Mavic 3E vs. Zenmuse L1 (Cloud-to-Cloud) | Mean: 0.236 m, RMS: 0.337 m |
| Primary Deliverables | Point clouds (.las), 3D Textured Mesh (.obj), Cartographic Layouts (A4), DEM & 1 m Contours |

## 1. Introduction

Unmanned Aerial Systems (UAS) paired with Structure from Motion (SfM) and Multi-View Stereo (MVS) algorithms provide an agile, millimeter-to-centimeter level framework for generating dense point clouds, textured 3D surface meshes, and orthomosaics. These spatial products are vital for long-term monitoring, digital archiving, and structural conservation of vulnerable geoheritage monuments.

**Aim:** Map and document the Plaka Park fossil reserves across two spatial scales:
1. **Park-Scale Overview:** Regional landscape mapping (GSD 3.23 cm/px) using both photogrammetry and LiDAR.
2. **Site-Scale Inspection:** Ultra-high-resolution documentation (GSD 0.67 cm/px) of an exposed fossilized tree trunk site using low-altitude terrain-following photogrammetry.

### Study area

Plaka Park forms part of the Petrified Forest of Lesvos in the northeastern Aegean Sea, Greece. The site preserves Early Miocene silicified tree trunks buried in situ by volcanic pyroclastic flows. Declared a protected natural monument in 1985, it was a founding member of the European Geoparks Network (2000) and joined the UNESCO Global Geoparks Network in 2004.

![Location and overview of Plaka Park](Plaka_park.jpg)

## 2. Methodology

### 2.1 Field Data Collection & Georeferencing

All flight operations were conducted around solar noon on 26 April 2026 across the western section of the park. 
* **LiDAR Mission:** Flown with the DJI Matrice and Zenmuse L1 sensor covering both sections of the park.
* **Photogrammetric Mission:** Flown with the DJI Mavic 3 Enterprise (RGB) covering the western sector and specific target fossil enclosures.
* **Georeferencing:** Positions were referenced to **WGS 84 / UTM zone 35N (EPSG:32635)** using synchronized onboard GNSS positioning.

![West section of the park](west1.jpg)

### 2.2 Flight Planning

| Mission | Aircraft & Sensor | Altitude (AGL) | Flight Speed | Target GSD | Image Count | Mapped Area | Overlap (Front / Side) |
|---|---|---|---|---|---|---|---|
| Whole Park | Matrice (Zenmuse L1 LiDAR) | 80 m | 4.5 m/s | 2.18 cm/px | 165 | 113,439 m² | 80% / 20% |
| Western Section | Mavic 3E (RGB Wide) | 120 m | 8.0 m/s | 3.23 cm/px | 98 | 0.10 km² | 80% / 70% |
| Fossil Site 1 | Mavic 3E (RGB) | 25 m (terrain-follow) | 3.7 m/s | 0.67 cm/px | 94 | 324 m² | 90% / 85% |
| Fossil Site 2 | Mavic 3E (RGB) | 25 m (terrain-follow) | 3.7 m/s | 0.67 cm/px | 65 | 721 m² | 90% / 85% |
| Fossil Site 3 | Mavic 3E (RGB) | 25 m (terrain-follow) | 3.7 m/s | 0.67 cm/px | 56 | 682 m² | 90% / 85% |

*Fossil Site 3 (fossilized logs 4 through 8) was selected as the reference target for multi-scale point cloud alignment and high-density 3D reconstruction.*

**Ground Sampling Distance Formula:**  
$$GSD = \frac{H \cdot S_w}{f \cdot IM_w}$$  
*(where $H$ = flight height, $S_w$ = sensor width, $f$ = focal length, and $IM_w$ = image width in pixels).*

#### Whole Park Survey: DJI Matrice (Zenmuse L1)
Flown at 80 m AGL in a nadir grid pattern with 80% frontal and 20% side overlap (total flight duration: 12 min 07 s). Total coverage was 113,439 m² with a point cloud sampling resolution of 2.18 cm/px.

![Flight plan, Matrice with Zenmuse L1](UAV_flight_plan_L1.png)  
*Figure 1: Automated flight trajectory for Matrice / Zenmuse L1 LiDAR acquisition.*

#### Western Section & Detail Sites: DJI Mavic 3 Enterprise
The regional park extent was flown at 120 m AGL at 8 m/s (5 min 11 s duration, 2.44 km flight path, 98 images). Detailed site surveys were flown at 25 m AGL utilizing automated real-time terrain-following altitude control to maintain a constant 0.67 cm/px GSD across sloping ground.

![Flight plan, Mavic 3E Wide](UAV_flight_plan.png)  
*Figure 2: Terrain-following flight trajectory for the Mavic 3 Enterprise detail surveys.*

### 2.3 Data Processing Workflow

1. **Photogrammetric Reconstruction (Agisoft Metashape):** Separate photo alignment pipelines were computed for park-scale and site-scale datasets. Dense point clouds were extracted using high-quality depth maps, followed by continuous 3D triangular mesh reconstruction, photographic texture projection, and true orthomosaic generation.
2. **Quantitative Cloud Comparison (CloudCompare):** Point clouds were exported as `.las` datasets. Two independent Cloud-to-Cloud (C2C) distance analyses were executed:
   - *Cross-Sensor Comparison:* Regional Mavic 3E photogrammetric cloud vs. Zenmuse L1 LiDAR cloud.
   - *Multi-Scale Comparison:* Regional Mavic 3E cloud vs. 25 m terrain-following fossil site cloud.
3. **Cartographic & Terrain Outputs (ArcGIS Pro):** Ground-classified LiDAR returns were used to generate a bare-earth Digital Elevation Model (DEM) and extract 1 m topographical contour lines. High-resolution orthophoto maps were composed and exported at standardized A4 print layouts.

---

## 3. Results

### 3.1 Point Cloud Densification

* **Park-Scale Cloud (120 m AGL):** 35,039,257 points (mean density: ~230 pts/m²).
* **Fossil-Site Cloud (25 m AGL terrain-following):** 34,388,203 points (mean density: 18,852 pts/m²).

![3D point cloud of the western part of the park](orthodytiko_2.png)  
*Figure 3: Overview point cloud of the western park sector.*

![3D point cloud of the fossil site](plaka_ortho_2.png)  
*Figure 4: Ultra-dense point cloud of Fossil Site 3 highlighting surface reconstruction of silicified tree trunks.*

### 3.2 3D Mesh Modeling

A high-fidelity surface mesh comprising 5.67 million triangular faces was generated and textured from original RAW exposures. A web-optimized version (573,774 faces) is interactively hosted on Sketchfab: **[mariapolchr on Sketchfab](https://sketchfab.com/mariapolchr)**.

![Textured 3D model of the fossil site](Fossil_1_Plaka_park.jpg)  
*Figure 5: High-resolution textured 3D triangular mesh model of the fossil enclosure.*

### 3.3 Cartographic Layouts

Standardized map layouts were compiled in ArcGIS Pro, providing both regional spatial context and millimeter-scale fossil monument detail.

![Orthophoto map of the fossil site](Fossils_Plaka_park.jpg)  
*Figure 6: High-resolution orthophoto detail layout of Fossil Site 3.*

![Orthophoto map of the western part of Plaka Park](Plaka_park_west_orthomap.jpg)  
*Figure 7: Regional overview orthophoto layout of the western park sector.*

![Fossil positions in Plaka Park](Fossil_positions_Plaka_park.jpg)  
*Figure 8: Spatial inventory map showing recorded fossil positions across Plaka Park.*

### 3.4 Digital Elevation Model (DEM) & Topography

Ground points classified from the Zenmuse L1 LiDAR survey provided the bare-earth surface model across the western sector, visualized with derived 1 m contour intervals.

![DEM and 1 m contours of the western part](DEM%26contour.jpg)  
*Figure 9: LiDAR-derived bare-earth DEM with 1 m elevation contours.*

---

### 3.5 Cloud-to-Cloud (C2C) Comparative Analysis

#### 3.5.1 Sensor Comparison: Mavic 3E (RGB) vs. Zenmuse L1 (LiDAR)
Surface density histograms demonstrate distinct sampling distributions: the LiDAR point cloud displays a wider, irregular distribution over complex terrain, whereas photogrammetric reconstruction shows a concentrated, uniform distribution.

<table>
  <tr>
    <td><img src="Histogram_Gauss_lidar_1.png" alt="Surface density histogram, Matrice L1"></td>
    <td><img src="Histogram_Gauss_lidar_2.png" alt="Number of neighbours histogram, Matrice L1"></td>
  </tr>
  <tr>
    <td align="center"><em>Surface Density: Matrice L1 LiDAR</em></td>
    <td align="center"><em>Neighbour Density: Matrice L1 LiDAR</em></td>
  </tr>
</table>

<table>
  <tr>
    <td><img src="Histogram_Gauss_plaka-ortho.png" alt="Surface density histogram, Mavic 3E"></td>
  </tr>
  <tr>
    <td align="center"><em>Surface Density: Mavic 3E Photogrammetry</em></td>
  </tr>
</table>

| Sensor / Metric | Mavic 3E (RGB) | Zenmuse L1 (LiDAR) |
|---|---|---|
| **Mean Point Density** | 236.6 pts/m² | 282.3 pts/m² |
| **Standard Deviation** | 28.3 | 92.0 |

![Cloud-to-cloud comparison, Mavic 3E vs Zenmuse L1](Mavic3E_vs_L1_C2C.png)  
*Figure 10: Spatial distribution of absolute C2C distance deviations between Mavic 3E and Zenmuse L1.*

<table>
  <tr>
    <td><img src="Histogram_Gauss_c2c.png" alt="Gauss histogram of C2C distances, Mavic 3E vs L1"></td>
    <td><img src="Histogram_C2C.png" alt="C2C histogram of absolute distances, Mavic 3E vs L1"></td>
  </tr>
  <tr>
    <td align="center"><em>Gaussian fit of C2C distances</em></td>
    <td align="center"><em>Absolute distance frequency distribution</em></td>
  </tr>
</table>

* **C2C Metrics (Photogrammetry vs. LiDAR):** Mean: **0.236 m** | Std. Dev: **0.240 m** | RMS: **0.337 m**.

---

#### 3.5.2 Multi-Scale Comparison: Regional Park vs. Detail Site (Mavic 3E)
Comparing the 120 m regional cloud with the 25 m terrain-following cloud confirms that reducing flight altitude increases local point density by approximately 80 times (~18,850 pts/m² vs. ~230 pts/m²).

<table>
  <tr>
    <td><img src="orthodytiko_sd.png" alt="Surface density histogram, park scale"></td>
    <td><img src="merged_sd.png" alt="Surface density histogram, fossil site"></td>
  </tr>
  <tr>
    <td align="center"><em>Surface density (120 m overview)</em></td>
    <td align="center"><em>Surface density (25 m terrain-follow)</em></td>
  </tr>
</table>

| Scale / Flight | Park Overview (120 m) | Fossil Site (25 m) |
|---|---|---|
| **Mean Point Density** | 230.5 pts/m² | 18,852 pts/m² |
| **Standard Deviation** | 32.6 | 3,751 |

![Cloud-to-cloud comparison, park vs site scale](Park_vs_fossil_C2C.png)  
*Figure 11: Cloud-to-cloud distance deviations between the 120 m regional cloud and 25 m detail cloud.*

* **C2C Metrics (Multi-Scale Alignment):** Mean: **0.054 m** | Std. Dev: **0.046 m** | RMS: **0.070 m**.

---

## 4. Discussion & Interpretation

1. **Photogrammetry vs. LiDAR Discrepancies:**  
   The $0.236\text{ m}$ mean difference between the Mavic 3E and Zenmuse L1 clouds is concentrated around high-gradient vertical features (wire boundary fences and footpath retaining walls). LiDAR effectively penetrated boundary brush and registered thin wire profiles, whereas photogrammetric depth reconstruction smoothed vertical wire geometry into pseudo-surfaces. Over open barren ground, both sensors demonstrated close geometric agreement (<0.10 m).
2. **Multi-Scale Geometric Fidelity:**  
   Comparing the 120 m overview survey and the 25 m terrain-following mission produced sub-decimeter consistency (mean: $0.054\text{ m}$, RMS: $0.070\text{ m}$). This proves that multi-altitude SfM acquisitions can be aligned into a seamless, multi-resolution spatial archive without scale distortion.
3. **Operational Trade-offs:**  
   While LiDAR provides direct bare-earth penetration through Mediterranean macchia vegetation to produce clean DEM contours, high-overlap RGB photogrammetry remains indispensable for sub-centimeter visual inspection, surface texturing, and structural crack documentation.

---

## 5. Limitations

* **Relative vs. Absolute Geodetic Accuracy:** Cloud-to-cloud comparisons evaluate relative agreement between point sets. Absolute spatial accuracy was constrained by onboard GNSS positions without independent terrestrial check points (CPs).
* **Multi-Parameter Sensor Variance:** The Mavic 3E vs. Zenmuse L1 comparison evaluates distinct flight heights (120 m vs. 80 m) and flight patterns simultaneously, reflecting real-world operational workflows rather than an isolated sensor benchmark.

---

## Tools & Environments

* **Platforms & Sensors:** DJI Mavic 3 Enterprise (Mechanical Shutter RGB), DJI Matrice 300 / Zenmuse L1 (LiDAR + RGB)
* **Photogrammetry:** Agisoft Metashape Professional
* **Point Cloud Processing:** CloudCompare (C2C Distance Computation, Density Histograms)
* **GIS & Cartography:** ArcGIS Pro (DEM Interpolation, Surface Contouring, Layout Composition)
* **3D Visualization:** Sketchfab

---

## References

1. Kelepertzis, E., Roussos, A., Drougas, C., Kypritidou, Z., Vassilakis, E., & Zouros, N. (2026). Soil geochemical patterns in Lesvos island UNESCO Global Geopark, Greece: Unveiling the influence of diverse geology. *Applied Geochemistry*, 205. https://doi.org/10.1016/j.apgeochem.2026.106893
2. Kotis, K., Angelis, S., Moraitou, E., Kopsachilis, V., Papadopoulou, E. E., Soulakellis, N., & Vaitis, M. (2023). A KG-Based Integrated UAV Approach for Engineering Semantic Trajectories in the Cultural Heritage Documentation Domain. *Remote Sensing*, 15(3). https://doi.org/10.3390/rs15030821
3. Papadopoulou, E. E., Papakonstantinou, A., Kapogianni, N. A., Zouros, N., & Soulakellis, N. (2022a). VR Multiscale Geovisualization Based on UAS Multitemporal Data: The Case of Geological Monuments. *Remote Sensing*, 14(17). https://doi.org/10.3390/rs14174259
4. Papadopoulou, E. E., Papakonstantinou, A., Vasilakos, C., Zouros, N., Tataris, G., Proestakis, S., & Soulakellis, N. (2022b). Scale issues for geoheritage 3D mapping: The case of Lesvos Geopark, Greece. *International Journal of Geoheritage and Parks*, 10(3), 435-446. https://doi.org/10.1016/j.ijgeop.2022.08.006
5. Pe-Piper, G., Piper, D. J. W., Anastasakis, G., Zouros, N., & Lyras, G. (2024). Variability in mineralization of the petrified forests in the UNESCO Global Geopark of Lesvos, Greece. *Marine and Petroleum Geology*, 167. https://doi.org/10.1016/j.marpetgeo.2024.106990
6. Zouros, N. C. (2021). The Miocene Petrified Forest of Lesvos, Greece: Research and Geoconservation Activities. *Geoconservation Research*, 4(2), 635-649. https://doi.org/10.30486/gcr.2021.1927340.1090

---
*Project developed at the University of the Aegean, Department of Geography.*
