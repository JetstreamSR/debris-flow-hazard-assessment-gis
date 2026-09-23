# Detailed method

## Spatial preparation

### Drainage extraction and Google Earth Pro interpretation

The initial valley lines and watershed context were prepared in ArcGIS and compared with Landsat 8 imagery. They were exported with **Layer To KML** for inspection in Google Earth Pro, where high-resolution imagery and the 3D terrain view supported manual checking of valley bottoms, ridge lines, tributary connections, and drainage divides.

Seven main gullies were identified and numbered. These main units were then subdivided into 18 polygons. The Google Earth interpretation was saved as KMZ and imported back into ArcGIS with **KML To Layer**. The converted polygon layer contained one feature for each named sub-catchment and served as the common zone layer for the analysis.

### ArcGIS data organization

The working geodatabase retained both the 18-unit polygon layer and intermediate tables. Surviving project artifacts confirm the following operations and outputs:

- an 18-feature sub-catchment polygon layer containing the `S1`-`S9` fields;
- zonal-statistics tables for slope, elevation, and precipitation;
- channel-length and straight-line-length tables;
- clipped geological polygons and intersection results;
- area statistics used to derive an area-weighted lithologic hardness coefficient;
- manually interpreted loose-material polygons and their intersection with all 18 assessment units.

Layers requiring area and length measurements were handled in a projected coordinate system. Intermediate tables were joined by sub-catchment name so that all nine indicator values could be stored in the final polygon attribute table.

## Indicator calculation

| Code | Indicator | Calculation |
| --- | --- | --- |
| S1 | Watershed area | Area of each sub-catchment polygon, expressed in km² |
| S2 | Mean slope | Mean value of the slope raster within each polygon |
| S3 | Channel length | Length of the mapped channel line within the assessment unit |
| S4 | Longitudinal gradient | `(maximum elevation - minimum elevation) / channel length` |
| S5 | Channel sinuosity | `mapped channel length / straight-line length` |
| S6 | Geomorphic information entropy | First calculate `S = (mean elevation - minimum elevation) / (maximum elevation - minimum elevation)`, then `H = S - 1 - ln(S)` |
| S7 | Maximum monthly precipitation | Maximum monthly precipitation value summarized for each polygon |
| S8 | Lithologic hardness coefficient | Sum of each rock unit's hardness index multiplied by its area proportion within the polygon |
| S9 | Loose-material proportion | Interpreted loose-material area divided by total sub-catchment area, expressed as a percentage |

Field Calculator was used for attribute-based calculations such as area conversion, ratios, and derived fields. Zonal Statistics as Table supplied raster summaries. Intersect, area calculations, summary statistics, and joins supported the geology and loose-material indicators. The attribute table was then exported for normalization and the final model calculations.

## Normalization

Nine indicators were normalized to remove differences in units and scales.

Positive normalization:

```text
x' = (x - xmin) / (xmax - xmin)
```

This was applied to mean slope (`S2`), channel length (`S3`), sinuosity (`S5`), maximum monthly precipitation (`S7`), and loose-material proportion (`S9`).

Negative normalization:

```text
x' = (xmax - x) / (xmax - xmin)
```

This was applied to watershed area (`S1`), longitudinal gradient (`S4`), geomorphic information entropy (`S6`), and lithologic hardness (`S8`) under the thesis's selected hazard-class definitions.

## CRITIC weighting

CRITIC weighting used two properties of every normalized indicator:

1. **contrast intensity**, represented by its standard deviation;
2. **conflict**, represented by its correlation with the other indicators.

Their combination produced the following weights:

| S1 | S2 | S3 | S4 | S5 | S6 | S7 | S8 | S9 |
| ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| 0.128 | 0.134 | 0.095 | 0.083 | 0.106 | 0.096 | 0.101 | 0.149 | 0.108 |

## Extension-theory classification

The model defined four reference classes for each normalized indicator: very high, high, medium, and low hazard. An extension correlation function measured how each sub-catchment's indicator value related to each class interval. The nine correlation values were combined with the CRITIC weights to produce four overall scores per sub-catchment.

The hazard class corresponding to the maximum overall correlation score was assigned to the sub-catchment. The final result contained 13 very-high-hazard units, one medium-hazard unit, and four low-hazard units.

## Map production

The classification table was joined to the 18-feature sub-catchment layer. ArcGIS was used to assign class colors, label assessment units, place the satellite basemap, and construct the final layout with a legend, north arrow, scale bar, and coordinate annotations. Separate layouts were also created for study-area location, elevation, lithologic hardness, loose surface material, and the sub-catchment scheme.

## Result boundary

The output is a relative hazard classification for this case study. Comparison with the documented 2020 event provides a spatial consistency check, but it does not constitute an independent predictive validation or a general-purpose operational warning model.

The detailed indicator table and source geospatial layers are not part of the public release. Several archived layers lack recoverable provider or redistribution records, and the thesis acknowledgement states that most raw data were supplied by a senior student for the academic project. See [`../DATA_SOURCES.md`](../DATA_SOURCES.md) for the provenance audit.
