# Data provenance and public-release scope

This note records what can and cannot be established from the archived thesis materials. It is intended to prevent the public portfolio from implying ownership of third-party source data.

## Provenance found in the archive

| Material used in the thesis | What can be established | Public-repository decision |
| --- | --- | --- |
| Monthly precipitation rasters, 2015–2019 | NetCDF metadata identifies Hohai University and the dataset *Monthly precipitation data set with 1 km resolution in China from 1960 to 2020*, DOI [`10.11922/sciencedb.01607`](https://doi.org/10.11922/sciencedb.01607). The dataset page lists CC BY-NC-ND 4.0. | Raw rasters and unit-level precipitation values are omitted. |
| Optical imagery | The thesis describes Landsat 8 as the optical reference. [USGS permits Landsat reuse and redistribution with source acknowledgement](https://www.usgs.gov/faqs/are-there-any-restrictions-use-or-redistribution-landsat-data), but the surviving 30 m GeoTIFFs have generic filenames and no product identifier or download metadata, so the exact USGS scene cannot be verified. | Images and source rasters are omitted. |
| Google Earth Pro imagery | Used for visual inspection, 3D terrain review, and manual checking of drainage divides. Google's [Geo Guidelines](https://about.google/brand-resource-center/products-and-services/geo-guidelines/) require visible attribution and restrict promotional use of Google Earth imagery. | Screenshots and KMZ/KML source files are omitted from the public repository. The README uses redrawn schematics without imagery. |
| DEM | The surviving 30 m raster contains coordinate and elevation information but no provider, product ID, or licence record. | Source raster and derived elevation figure are omitted. |
| Geological polygons | The layer metadata shows that it came through the academic collaborator who supplied most raw data. The thesis cites Zhang Ji (2022) for the regional geological context, but the archived layer does not identify a distributable source dataset or licence. | Layer and unit-level lithology values are omitted. |
| Watershed and drainage source layers | The archived lineage records local processing paths but not the original provider or licence. | Source layers are omitted. |
| Assessment polygons and final classes | The polygons reflect the author's interpretation and thesis workflow; the classes are the author's model output. | Displayed only as schematics without third-party basemaps. The final result table is included. |

## Important authorship boundary

The thesis acknowledgement states that a senior student provided most of the raw data used in the study. Those files were suitable for the original supervised academic project, but the archive does not contain permission to redistribute them publicly. Their absence from this repository is therefore deliberate.

Two thesis figures credited to earlier literature were also excluded: the regional geological map cited from Zhang Ji (2022) and the before/after disaster imagery cited from Wen Qiang (2022).

## References recorded by the thesis

- Zheng Wanmo. *Detailed Investigation Report on Geological Hazards in Danba County, Sichuan Province*. Chengdu Center, China Geological Survey, 2006.
- Zhang Ji. *Early Identification of Debris-Flow-Prone Areas and Debris-Flow Hazard Assessment in Danba County*. Southwest Jiaotong University, 2022. DOI: `10.27414/d.cnki.gxnju.2022.003078`.
- Wen Qiang. *Formation Mechanism and Hazard Assessment of the Meilonggou Debris Flow in Danba County*. Southwest Jiaotong University, 2022. DOI: `10.27414/d.cnki.gxnju.2022.000990`.
- Qu Lisha, Zhu Qiuan, Zhu Chaofan, and Zhang Jiang. *Monthly precipitation data set with 1 km resolution in China from 1960 to 2020*. Science Data Bank, 2022. DOI: [`10.11922/sciencedb.01607`](https://doi.org/10.11922/sciencedb.01607).

No open-source or open-data licence is applied to this repository. Reuse of any third-party dataset must follow the original provider's terms.
