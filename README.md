# Multi-scale UAV Mapping of Plaka Park, Lesvos Petrified Forest Geopark

Mapping the western part of Plaka Park (Lesvos UNESCO Global Geopark) at two scales, the whole park section (1:100) and a single fossil site (1:10), using drone photogrammetry (RGB) and LiDAR. Outputs are point clouds, a textured 3D model, orthophoto maps and a DEM with contours, plus a comparison of the point clouds.

![Orthophoto map of the western part of Plaka Park](Plaka_park_west_orthomap.jpg)

## Key results

| | |
|---|---|
| Fieldwork date | 26 April 2026 |
| Sensors | DJI Mavic 3 Enterprise (RGB) and DJI Matrice with Zenmuse L1 (LiDAR) |
| Park-scale point cloud (Mavic 3E) | 35.0 million points, GSD 3.23 cm/px |
| Fossil-site point cloud (Mavic 3E) | 34.4 million points, GSD 0.67 cm/px |
| Park vs fossil site, cloud-to-cloud | mean 0.054 m, RMS 0.070 m |
| Mavic 3E vs Zenmuse L1, cloud-to-cloud | mean 0.236 m, RMS 0.337 m |
| Outputs | Point clouds, textured 3D model, two A4 orthophoto maps, DEM with 1 m contours |

## Study area

Plaka Park is part of the Petrified Forest of Lesvos in the northeastern Aegean. The forest preserves fossilised trees buried by volcanic ash and pyroclastic flows during the Early Miocene, and was declared a protected natural monument in 1985. It joined the European Geoparks Network in 2000 and the UNESCO Global Geoparks Network in 2004.

![Location and overview of Plaka Park](Plaka_park.jpg)

## Data collection

All flights took place around midday on 26 April 2026 in the western part of the park.

| Flight | Aircraft and sensor | Height | Speed | GSD | Images | Area | Overlap (front/side) |
|---|---|---|---|---|---|---|---|
| Whole park (both parts) | Matrice, Zenmuse L1 LiDAR | 80 m | 4.5 m/s | 2.18 cm/px | 165 | 113,439 m² | 80% / 20% |
| Western part | Mavic 3E Wide | 120 m | 8 m/s | 3.23 cm/px | 98 | 0.10 km² | 80% / 70% |
| Fossil site 1 | Mavic 3E | 25 m (terrain follow) | 3.7 m/s | 0.67 cm/px | 94 | 324 m² | 90% / 85% |
| Fossil site 2 | Mavic 3E | 25 m (terrain follow) | 3.7 m/s | 0.67 cm/px | 65 | 721 m² | 90% / 85% |
| Fossil site 3 | Mavic 3E | 25 m (terrain follow) | 3.7 m/s | 0.67 cm/px | 56 | 682 m² | 90% / 85% |

Site 3 (logs 4 to 8) was chosen as the reference site for the detailed processing. GSD is computed as `GSD = (H · Sw) / (f · IMw)`, where H is flight height, Sw is sensor width, f is focal length and IMw is image width in pixels.

![Flight plan for site 3](flight_plan_site3.png) <!-- upload this image -->

## Processing

1. **Photogrammetry (Agisoft Metashape):** imported and aligned the photos of the park and the fossil site separately, built a dense point cloud, then a 3D mesh, texture and orthomosaic.
2. **Cloud comparison (CloudCompare):** exported the point clouds as `.las` and ran two independent cloud-to-cloud (C2C) comparisons: (1) the park-scale Mavic 3E cloud against the Zenmuse L1 LiDAR cloud, and (2) the park-scale Mavic 3E cloud against the fossil-site Mavic 3E cloud, cropped to the area where they overlap.
3. **Mapping:** produced A4 orthophoto maps at 1:100 (park section) and 1:10 (fossil site). Generated a DEM from the LiDAR point cloud and extracted 1 m contour lines `[QGIS / ArcGIS]`.

![West section of the park](west1.jpg)

## Results

### Point clouds

The park-scale cloud has 35,039,257 points and the fossil-site cloud has 34,388,203, both at high quality in Metashape.

![3D point cloud of the western part of the park](point_cloud_west.png) <!-- upload this image -->

At 25 m flight height the fossil site is far denser: about 18,850 points/m² compared with about 230 points/m² for the park-scale cloud.

![3D point cloud of the fossil site](point_cloud_site.png) <!-- upload this image -->

### 3D model of the fossil site

A high-resolution mesh (5.67 million faces) was built from the point cloud, textured from the original images and cropped around the fenced site. A medium-quality version (573,774 faces) is available on Sketchfab: [SKETCHFAB LINK].

![Textured 3D model of the fossil site](model_site_textured.png) <!-- upload this image -->

### Orthophoto maps

The 1:10 map shows the fossil trunks in fine detail, and the 1:100 map (at the top of this page) gives the general picture of the western zone.

![Orthophoto map of the fossil site](Fossils_Plaka_park.jpg)

![Fossil positions in Plaka Park](Fossil_positions_Plaka_park.jpg)

### DEM and contours

The DEM from the L1 LiDAR cloud covers the western section, with 1 m contour lines showing the terrain.

![DEM and contour map of the western part](dem_contours.png) <!-- upload this image -->

## Cloud comparison

### Mavic 3E (photogrammetry) vs Zenmuse L1 (LiDAR)

| | Mavic 3E | Zenmuse L1 |
|---|---|---|
| Mean density | 236.6 points/m² | 282.3 points/m² |
| Std. deviation | 28.3 | 92.0 |

The photogrammetric cloud is evenly distributed, while the LiDAR cloud is denser on average but much more uneven. The C2C distance has a mean of 0.236 m (std 0.240 m, RMS 0.337 m). Most distances are below 0.5 m, and the largest differences appear along the fence and paths, where the two methods capture vertical structures differently. Over open ground and vegetation the agreement is good.

![Cloud-to-cloud comparison, Mavic 3E vs Zenmuse L1](c2c_mavic_vs_l1.png) <!-- upload this image -->

### Park scale vs fossil-site scale (both Mavic 3E)

The C2C distance has a mean of 0.054 m (std 0.046 m, RMS 0.070 m), with most values below 0.1 m. The only visible differences are along the fence, so the two scales agree well geometrically.

![Cloud-to-cloud comparison, park vs site scale](c2c_scale_comparison.png) <!-- upload this image -->

## Limitations

- C2C distance measures how well two clouds agree with each other, not how accurate either one is against the ground. `[State whether ground control points or RTK were used for georeferencing.]`
- The Mavic 3E vs L1 comparison mixes two methods, two flight heights and two flight patterns, so it can't isolate the effect of the sensor.
- Only one fossil site (site 3) was processed in detail, and data were collected on a single day.
- The A4 maps were made at two fixed scales and are not a continuous multi-scale product.

## Tools

DJI Mavic 3 Enterprise, DJI Matrice with Zenmuse L1 `[model]`, Agisoft Metashape, CloudCompare, `[QGIS / ArcGIS Pro]`, Sketchfab.

## Repository contents

- `*.jpg`: maps and images used in this README
- `Geopark.pdf`, `Plaka_Park.pdf`, `plaka_location.pdf`: map layouts as PDF

## Reference

Papadopoulou, E. E., Papakonstantinou, A., Vasilakos, C., Zouros, N., Tataris, G., Proestakis, S., & Soulakellis, N. (2022). Scale issues for geoheritage 3D mapping: The case of Lesvos Geopark, Greece. *International Journal of Geoheritage and Parks*, 10(3), 435-446. https://doi.org/10.1016/j.ijgeop.2022.08.006

*Project developed at the University of the Aegean, Department of Geography.*
