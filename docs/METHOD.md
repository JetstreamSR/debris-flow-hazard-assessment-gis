# Method summary

## Assessment units

The Meilonggou watershed was interpreted as seven main gullies and subdivided into 18 sub-catchments. These sub-catchments served as the common spatial units for indicator calculation and hazard classification.

## Indicators

| Code | Indicator | Role in the assessment |
| --- | --- | --- |
| S1 | Watershed area | Catchment-scale contributing area |
| S2 | Mean slope | General terrain steepness |
| S3 | Channel length | Scale of the drainage path |
| S4 | Longitudinal gradient | Channel relief relative to length |
| S5 | Channel sinuosity | Planimetric channel geometry |
| S6 | Geomorphic information entropy | Longitudinal-profile development |
| S7 | Maximum monthly precipitation | Rainfall trigger condition |
| S8 | Lithologic hardness | Geological resistance proxy |
| S9 | Loose-material proportion | Availability of mobilizable material |

## Processing and assessment

1. Drainage lines, watershed boundaries, and sub-catchments were prepared in ArcGIS and visually checked with remote-sensing imagery.
2. Terrain, channel, rainfall, geological, and surface-material attributes were joined to the 18 assessment units.
3. Indicator values were calculated and organized using ArcGIS Field Calculator and tables.
4. Positive and negative indicators were normalized to a common scale.
5. CRITIC weighting represented both the variability of each indicator and its conflict with the other indicators.
6. Extension-theory correlation functions compared every assessment unit with four hazard classes.
7. The class with the maximum correlation value was assigned to each sub-catchment and mapped in ArcGIS.

## Indicator weights

| S1 | S2 | S3 | S4 | S5 | S6 | S7 | S8 | S9 |
| ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| 0.128 | 0.134 | 0.095 | 0.083 | 0.106 | 0.096 | 0.101 | 0.149 | 0.108 |

## Result boundary

The output is a relative hazard classification for this case study. Comparison with the documented 2020 event provides a spatial consistency check, but it does not constitute an independent predictive validation or a general-purpose operational warning model.

